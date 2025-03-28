<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Machine Information Admin Portal</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
        }
        
        .container {
            width: 95%;
            margin: 0 auto;
            min-height: 100vh;
            position: relative;
            padding-bottom: 60px;
        }
        
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 80vh;
        }
        
        .login-form {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(0,0,0,0.1);
            width: 350px;
        }
        
        .login-form h2 {
            text-align: center;
            margin-bottom: 25px;
            color: #333;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #555;
        }
        
        .form-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        
        .btn {
            background-color: #4CAF50;
            color: white;
            padding: 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            font-weight: bold;
            transition: background-color 0.3s;
        }
        
        .btn:hover {
            background-color: #45a049;
        }
        
        .dashboard {
            display: none;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(0,0,0,0.1);
            padding: 20px;
            margin-top: 20px;
        }
        
        .header {
            background-color: #4CAF50;
            color: white;
            padding: 15px 20px;
            border-radius: 8px 8px 0 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .user-actions {
            display: flex;
            gap: 15px;
        }
        
        .user-actions a {
            color: white;
            text-decoration: none;
            font-size: 14px;
        }
        
        .stats {
            display: flex;
            justify-content: space-between;
            margin: 25px 0;
            gap: 15px;
        }
        
        .stat-box {
            background-color: #f9f9f9;
            padding: 15px;
            border-radius: 6px;
            text-align: center;
            flex: 1;
            box-shadow: 0 0 5px rgba(0,0,0,0.05);
        }
        
        .stat-box h3 {
            margin-top: 0;
            color: #4CAF50;
            font-size: 16px;
        }
        
        .stat-box p {
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 0;
            color: #333;
        }
        
        .form-section {
            background-color: #f9f9f9;
            padding: 20px;
            border-radius: 6px;
            margin-bottom: 25px;
        }
        
        .form-section h2 {
            margin-top: 0;
            color: #333;
            font-size: 20px;
        }
        
        .form-row {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .form-row .form-group {
            flex: 1;
        }
        
        textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-family: Arial, sans-serif;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 25px 0;
        }
        
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        th {
            background-color: #4CAF50;
            color: white;
            position: sticky;
            top: 0;
        }
        
        tr:hover {
            background-color: #f5f5f5;
        }
        
        .action-btn {
            padding: 6px 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 14px;
            margin-right: 5px;
        }
        
        .accept-btn {
            background-color: #4CAF50;
            color: white;
        }
        
        .hold-btn {
            background-color: #FF9800;
            color: white;
        }
        
        .delete-btn {
            background-color: #f44336;
            color: white;
        }
        
        .photo-preview {
            width: 50px;
            height: 50px;
            object-fit: cover;
            border-radius: 4px;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 100;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background-color: white;
            padding: 25px;
            border-radius: 8px;
            width: 90%;
            max-width: 500px;
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .close {
            font-size: 24px;
            cursor: pointer;
        }
        
        .global-footer {
            text-align: center;
            padding: 15px;
            background-color: gray;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
            font-size: 14px;
        }
        
        .table-container {
            max-height: 400px;
            overflow-y: auto;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 6px;
        }
    </style>
</head>
<body>
    <!-- Global Footer -->
    <footer class="global-footer">
        All Rights Reserved by Dev Makwana Ebixserver 2025
    </footer>

    <div class="container">
        <!-- Login Section -->
        <div class="login-container" id="loginSection">
            <div class="login-form">
                <h2>Admin Login</h2>
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" placeholder="Enter username">
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" placeholder="Enter password">
                </div>
                <button class="btn" onclick="login()">Login</button>
            </div>
        </div>
        
        <!-- Dashboard Section -->
        <div class="dashboard" id="dashboard">
            <div class="header">
                <h1>Machine Information Admin Portal</h1>
                <div class="user-actions">
                    <span id="displayUsername">eraj12</span>
                    <a href="#" onclick="showChangePasswordModal()">Change Password</a>
                    <a href="#" onclick="logout()">Logout</a>
                </div>
            </div>
            
            <div class="stats">
                <div class="stat-box">
                    <h3>Total Records</h3>
                    <p id="totalRecords">0</p>
                </div>
                <div class="stat-box">
                    <h3>Accepted Records</h3>
                    <p id="acceptedRecords">0</p>
                </div>
                <div class="stat-box">
                    <h3>Hold Records</h3>
                    <p id="holdRecords">0</p>
                </div>
            </div>
            
            <div class="form-section">
                <h2>Add New Machine Record</h2>
                <div class="form-row">
                    <div class="form-group">
                        <label for="machineName">Machine Name</label>
                        <input type="text" id="machineName" placeholder="Enter machine name">
                    </div>
                    <div class="form-group">
                        <label for="serialNumber">Serial Number</label>
                        <input type="text" id="serialNumber" placeholder="Enter serial number">
                    </div>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="machinePhoto">Upload Photo</label>
                        <input type="file" id="machinePhoto" accept="image/*">
                    </div>
                    <div class="form-group">
                        <label for="recordType">Record Type</label>
                        <select id="recordType" style="width: 100%; padding: 10px; height: 40px;">
                            <option value="Purchase">Purchase</option>
                            <option value="Service">Service</option>
                            <option value="Warranty">Warranty</option>
                        </select>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="remarks">Remarks</label>
                    <textarea id="remarks" rows="3" placeholder="Enter any remarks"></textarea>
                </div>
                
                <button class="btn" onclick="addRecord()">Add Record</button>
            </div>
            
            <h2>Machine Records</h2>
            <div class="table-container">
                <table id="recordsTable">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Machine Name</th>
                            <th>Serial Number</th>
                            <th>Photo</th>
                            <th>Type</th>
                            <th>Status</th>
                            <th>Created At</th>
                            <th>Updated At</th>
                            <th>Remarks</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody>
                        <!-- Records will be added here dynamically -->
                    </tbody>
                </table>
            </div>
        </div>
        
        <!-- Change Password Modal -->
        <div id="changePasswordModal" class="modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h2>Change Password</h2>
                    <span class="close" onclick="closeModal('changePasswordModal')">&times;</span>
                </div>
                <div class="form-group">
                    <label for="currentPassword">Current Password</label>
                    <input type="password" id="currentPassword" placeholder="Enter current password">
                </div>
                <div class="form-group">
                    <label for="newPassword">New Password</label>
                    <input type="password" id="newPassword" placeholder="Enter new password">
                </div>
                <div class="form-group">
                    <label for="confirmPassword">Confirm New Password</label>
                    <input type="password" id="confirmPassword" placeholder="Confirm new password">
                </div>
                <button class="btn" onclick="changePassword()">Change Password</button>
            </div>
        </div>
        
        <!-- Hold Record Modal -->
        <div id="holdRecordModal" class="modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h2>Put Record on Hold</h2>
                    <span class="close" onclick="closeModal('holdRecordModal')">&times;</span>
                </div>
                <div class="form-group">
                    <label for="holdRemarks">Reason for Hold</label>
                    <textarea id="holdRemarks" rows="3" placeholder="Enter reason for putting this record on hold"></textarea>
                </div>
                <button class="btn hold-btn" onclick="confirmHold()">Confirm Hold</button>
            </div>
        </div>
    </div>

    <script>
        // Database simulation using localStorage
        let records = JSON.parse(localStorage.getItem('machineRecords')) || [];
        let currentUser = null;
        let currentHoldId = null;
        
        // Default user
        const defaultUser = {
            username: 'eraj12',
            password: '12345'
        };
        
        // Initialize the app
        function init() {
            // Check if user is already logged in
            const loggedInUser = localStorage.getItem('loggedInUser');
            if (loggedInUser) {
                currentUser = JSON.parse(loggedInUser);
                showDashboard();
                updateStats();
                displayRecords();
            }
            
            // Set default user if not exists
            if (!localStorage.getItem('users')) {
                localStorage.setItem('users', JSON.stringify([defaultUser]));
            }
        }
        
        // Login function
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            const users = JSON.parse(localStorage.getItem('users'));
            const user = users.find(u => u.username === username && u.password === password);
            
            if (user) {
                currentUser = user;
                localStorage.setItem('loggedInUser', JSON.stringify(user));
                showDashboard();
                updateStats();
                displayRecords();
            } else {
                alert('Invalid username or password');
            }
        }
        
        // Logout function
        function logout() {
            currentUser = null;
            localStorage.removeItem('loggedInUser');
            document.getElementById('loginSection').style.display = 'flex';
            document.getElementById('dashboard').style.display = 'none';
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
        }
        
        // Show dashboard
        function showDashboard() {
            document.getElementById('loginSection').style.display = 'none';
            document.getElementById('dashboard').style.display = 'block';
            document.getElementById('displayUsername').textContent = currentUser.username;
        }
        
        // Add new record
        function addRecord() {
            const machineName = document.getElementById('machineName').value;
            const serialNumber = document.getElementById('serialNumber').value;
            const photoInput = document.getElementById('machinePhoto');
            const recordType = document.getElementById('recordType').value;
            const remarks = document.getElementById('remarks').value;
            
            if (!machineName || !serialNumber) {
                alert('Machine name and serial number are required');
                return;
            }
            
            let photo = null;
            if (photoInput.files.length > 0) {
                const file = photoInput.files[0];
                photo = URL.createObjectURL(file);
            }
            
            const newRecord = {
                id: Date.now(),
                machineName,
                serialNumber,
                photo,
                recordType,
                status: 'Pending',
                createdAt: new Date().toLocaleString(),
                updatedAt: new Date().toLocaleString(),
                remarks,
                updatedBy: currentUser.username
            };
            
            records.push(newRecord);
            saveRecords();
            
            // Clear form
            document.getElementById('machineName').value = '';
            document.getElementById('serialNumber').value = '';
            document.getElementById('machinePhoto').value = '';
            document.getElementById('remarks').value = '';
            
            updateStats();
            displayRecords();
        }
        
        // Update record status
        function updateRecordStatus(id, status, remarks = '') {
            const record = records.find(r => r.id === id);
            if (record) {
                record.status = status;
                record.updatedAt = new Date().toLocaleString();
                record.updatedBy = currentUser.username;
                if (remarks) {
                    record.remarks = remarks;
                }
                saveRecords();
                updateStats();
                displayRecords();
            }
        }
        
        // Delete record
        function deleteRecord(id) {
            if (confirm('Are you sure you want to delete this record?')) {
                records = records.filter(r => r.id !== id);
                saveRecords();
                updateStats();
                displayRecords();
            }
        }
        
        // Show hold record modal
        function showHoldModal(id) {
            currentHoldId = id;
            document.getElementById('holdRemarks').value = '';
            document.getElementById('holdRecordModal').style.display = 'flex';
        }
        
        // Confirm hold
        function confirmHold() {
            const remarks = document.getElementById('holdRemarks').value;
            if (!remarks) {
                alert('Please enter a reason for hold');
                return;
            }
            
            updateRecordStatus(currentHoldId, 'Hold', remarks);
            closeModal('holdRecordModal');
        }
        
        // Show change password modal
        function showChangePasswordModal() {
            document.getElementById('currentPassword').value = '';
            document.getElementById('newPassword').value = '';
            document.getElementById('confirmPassword').value = '';
            document.getElementById('changePasswordModal').style.display = 'flex';
        }
        
        // Change password
        function changePassword() {
            const currentPassword = document.getElementById('currentPassword').value;
            const newPassword = document.getElementById('newPassword').value;
            const confirmPassword = document.getElementById('confirmPassword').value;
            
            if (currentPassword !== currentUser.password) {
                alert('Current password is incorrect');
                return;
            }
            
            if (newPassword !== confirmPassword) {
                alert('New passwords do not match');
                return;
            }
            
            const users = JSON.parse(localStorage.getItem('users'));
            const userIndex = users.findIndex(u => u.username === currentUser.username);
            
            if (userIndex !== -1) {
                users[userIndex].password = newPassword;
                localStorage.setItem('users', JSON.stringify(users));
                
                // Update current user
                currentUser.password = newPassword;
                localStorage.setItem('loggedInUser', JSON.stringify(currentUser));
                
                alert('Password changed successfully');
                closeModal('changePasswordModal');
            }
        }
        
        // Close modal
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }
        
        // Save records to localStorage
        function saveRecords() {
            localStorage.setItem('machineRecords', JSON.stringify(records));
        }
        
        // Update statistics
        function updateStats() {
            document.getElementById('totalRecords').textContent = records.length;
            document.getElementById('acceptedRecords').textContent = records.filter(r => r.status === 'Accepted').length;
            document.getElementById('holdRecords').textContent = records.filter(r => r.status === 'Hold').length;
        }
        
        // Display records in table
        function displayRecords() {
            const tbody = document.querySelector('#recordsTable tbody');
            tbody.innerHTML = '';
            
            records.forEach(record => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${record.id}</td>
                    <td>${record.machineName}</td>
                    <td>${record.serialNumber}</td>
                    <td>${record.photo ? `<img src="${record.photo}" class="photo-preview">` : 'No photo'}</td>
                    <td>${record.recordType}</td>
                    <td>${record.status}</td>
                    <td>${record.createdAt}</td>
                    <td>${record.updatedAt}</td>
                    <td>${record.remarks || '-'}</td>
                    <td>
                        ${record.status !== 'Accepted' ? `<button class="action-btn accept-btn" onclick="updateRecordStatus(${record.id}, 'Accepted')">Accept</button>` : ''}
                        ${record.status !== 'Hold' ? `<button class="action-btn hold-btn" onclick="showHoldModal(${record.id})">Hold</button>` : ''}
                        <button class="action-btn delete-btn" onclick="deleteRecord(${record.id})">Delete</button>
                    </td>
                `;
                
                tbody.appendChild(row);
            });
        }
        
        // Initialize the app when page loads
        window.onload = init;
    </script>
</body>
</html>
