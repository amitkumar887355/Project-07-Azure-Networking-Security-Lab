# Azure Networking & Security Lab – Validation Test Results

## Objective

To validate the functionality and security of the Azure networking components after deployment.

---

# Test 1 – Jump VM Remote Desktop Access

### Objective

Verify that the Jump VM is accessible from the Internet using RDP.

### Test Steps

1. Open Remote Desktop Connection.
2. Enter the Public IP of JUMP-VM.
3. Authenticate with administrator credentials.

### Expected Result

Remote Desktop session is established successfully.

### Actual Result

✅ Successfully connected to JUMP-VM.

**Status:** PASS

---

# Test 2 – Access Production VM through Jump VM

### Objective

Verify that the Production VM can only be accessed from the internal network.

### Test Steps

1. Connect to JUMP-VM.
2. Launch Remote Desktop Connection.
3. Connect to PROD-VM using its Private IP address.

### Expected Result

Connection is successful.

### Actual Result

✅ Successfully connected to PROD-VM.

**Status:** PASS

---

# Test 3 – Azure Bastion Connectivity

### Objective

Verify secure browser-based access to the Production VM.

### Test Steps

1. Open Azure Portal.
2. Select PROD-VM.
3. Connect using Azure Bastion.

### Expected Result

Browser-based RDP session opens successfully.

### Actual Result

✅ Azure Bastion connected successfully.

**Status:** PASS

---

# Test 4 – Network Security Group (NSG)

### Objective

Verify that inbound RDP is allowed.

### Test Steps

Attempt RDP to JUMP-VM.

### Expected Result

RDP connection succeeds.

### Actual Result

✅ RDP access allowed.

**Status:** PASS

---

# Test 5 – Outbound Internet Restriction

### Objective

Verify that outbound Internet access is blocked from JUMP-VM.

### Test Steps

Open a web browser on JUMP-VM and browse to multiple websites.

### Expected Result

Internet access is denied.

### Actual Result

✅ Internet access blocked.

**Status:** PASS

---

# Test 6 – Azure DDoS Protection

### Objective

Verify that the DDoS Protection Plan is associated with the virtual network.

### Test Steps

Open the Azure DDoS Protection Plan and confirm that Vnet01 is linked.

### Expected Result

Virtual network association is visible.

### Actual Result

✅ Vnet01 successfully associated with the Azure DDoS Protection Plan.

**Status:** PASS

---

# Test 7 – User Defined Route (UDR)

### Objective

Verify that traffic from the Production subnet is routed through Azure Firewall.

### Test Steps

Review the Route Table associated with the Production subnet.

### Expected Result

Default route (0.0.0.0/0) points to Azure Firewall.

### Actual Result

✅ Traffic routed through Azure Firewall.

**Status:** PASS

---

# Test 8 – Azure Firewall Application Rules

### Objective

Verify that only approved websites are accessible.

### Test Steps

From PROD-VM, browse to:

* google.com
* tcs.com
* ibm.com
* github.com
* facebook.com

### Expected Result

Approved websites open successfully.
Unapproved websites are blocked.

### Actual Result

| Website      | Result    |
| ------------ | --------- |
| google.com   | ✅ Allowed |
| tcs.com      | ✅ Allowed |
| ibm.com      | ✅ Allowed |
| github.com   | ❌ Blocked |
| facebook.com | ❌ Blocked |

**Status:** PASS

---

# Test 9 – Azure Firewall DNAT

### Objective

Verify remote administration through Azure Firewall.

### Test Steps

1. Open Remote Desktop Connection.
2. Connect to Azure Firewall Public IP using port 8080.
3. Verify translation to JUMP-VM on port 3389.

### Expected Result

RDP session connects to JUMP-VM.

### Actual Result

✅ Successfully connected to JUMP-VM using Azure Firewall DNAT.

**Status:** PASS

---

# Summary

| Test                             | Status |
| -------------------------------- | ------ |
| Jump VM RDP                      | ✅ PASS |
| Production VM via Jump VM        | ✅ PASS |
| Azure Bastion                    | ✅ PASS |
| NSG Inbound Rule                 | ✅ PASS |
| NSG Outbound Restriction         | ✅ PASS |
| Azure DDoS Association           | ✅ PASS |
| UDR Routing                      | ✅ PASS |
| Azure Firewall Application Rules | ✅ PASS |
| Azure Firewall DNAT              | ✅ PASS |

## Conclusion

The lab successfully implemented a secure Azure network architecture with network segmentation, controlled administrative access, centralized traffic inspection, application-level filtering, DDoS protection, and Azure Firewall DNAT. All validation tests completed successfully, demonstrating that the environment functions as designed and follows Azure networking and security best practices.
