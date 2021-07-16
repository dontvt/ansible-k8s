# ansible-k8s

# Chuẩn bị: 
- Server master và node. 
- Có user ubuntu có quyền sudo và có thư mục home
- Cấu hình ~./ssh/config để ssh vào server. 
- Update thông tin vào file host của ansible.

# Run: 
- Cài đặt các gói phụ thuộc chạy trên all server. 
```bash
ansible-playbook -v  -i inventory/k8s/ playbooks/k8s_kubeadm/initialize-playbook.yml
```


- Khởi tạo Cluster với 1 node master ban đâu: 
```bash
ansible-playbook -v  -i inventory/k8s/ playbooks/k8s_kubeadm/cluster-playbook.yml
```
Lưu ý: update  IP của LB.


- joint node vào cluster: 
```bash
ansible-playbook -v  -i inventory/k8s/ playbooks/k8s_kubeadm/node-playbook.yml
```

- joint thêm master vào cluster
```bash
ansible-playbook -v  -i inventory/k8s/ playbooks/k8s_kubeadm/master-playbook.yml
```

