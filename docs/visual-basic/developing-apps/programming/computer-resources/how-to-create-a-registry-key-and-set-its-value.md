---
title: 'Nasıl Yapılır: Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 459c4b3f971009ee4b6b669c55bc058db0826595
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349195"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="0b9ad-102">Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="0b9ad-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="0b9ad-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="0b9ad-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="0b9ad-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="0b9ad-105">To create a registry key</span><span class="sxs-lookup"><span data-stu-id="0b9ad-105">To create a registry key</span></span>

- <span data-ttu-id="0b9ad-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="0b9ad-107">The parameter `Subkey` is not case-sensitive.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="0b9ad-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="0b9ad-109">To create a registry key and set a value in it</span><span class="sxs-lookup"><span data-stu-id="0b9ad-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="0b9ad-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="0b9ad-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="0b9ad-112">Set the value with the `SetValue` method.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="0b9ad-113">This example sets the string value.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-113">This example sets the string value.</span></span> <span data-ttu-id="0b9ad-114">"MyTestKeyValue" to "This is a test value".</span><span class="sxs-lookup"><span data-stu-id="0b9ad-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="0b9ad-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b9ad-115">Example</span></span>

<span data-ttu-id="0b9ad-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="0b9ad-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="0b9ad-117">Robust Programming</span></span>

<span data-ttu-id="0b9ad-118">Examine the registry structure to find a suitable location for your key.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="0b9ad-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="0b9ad-120">Then add the registry values to your company's key.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="0b9ad-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="0b9ad-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="0b9ad-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="0b9ad-123">When you create a registry value, you need to decide what to do if that value already exists.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="0b9ad-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="0b9ad-125">When you put data in the registry value, the data is available to the other process.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="0b9ad-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="0b9ad-127">It returns `Nothing` if the key does not already exist.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="0b9ad-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span><span class="sxs-lookup"><span data-stu-id="0b9ad-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="0b9ad-129">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="0b9ad-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="0b9ad-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0b9ad-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="0b9ad-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0b9ad-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="0b9ad-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0b9ad-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="0b9ad-133">The key is closed (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0b9ad-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="0b9ad-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="0b9ad-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="0b9ad-135">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0b9ad-135">.NET Framework Security</span></span>

<span data-ttu-id="0b9ad-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="0b9ad-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="0b9ad-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="0b9ad-139">For example, a local application that has the code access security permission might not have operating system permission.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="0b9ad-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="0b9ad-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b9ad-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b9ad-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="0b9ad-142">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="0b9ad-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="0b9ad-143">Code Access Security Basics</span><span class="sxs-lookup"><span data-stu-id="0b9ad-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
