# ansible-k8s

# Chuẩn bị: 
- Server master và node. 
- Có quyền sudo
- Cấu hình ~./ssh/config để ssh vào server. 
- Update thông tin vào file host của ansible.

# Run: 
- Cài đặt các gói phụ thuộc chạy trên all server. 
ansible-playbook -v  -i inventory/k8s/ playbooks/k8s_kubeadm/initialize-playbook.yml


- Khởi tạo Cluster với 1 node master ban đâu: 
ansible-playbook -v  -i inventory/k8s/ playbooks/k8s_kubeadm/cluster-playbook.yml
Lưu ý: update  IP của LB.


- joint node vào cluster: 
ansible-playbook -v  -i inventory/k8s/ playbooks/k8s_kubeadm/node-playbook.yml


- joint thêm master vào cluster
ansible-playbook -v  -i inventory/k8s/ playbooks/k8s_kubeadm/master-playbook.yml


