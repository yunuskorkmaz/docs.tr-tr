---
title: "Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6e71c106592490b92cf6f2dc02e59cddb28b95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="ab97e-102">Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="ab97e-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="ab97e-103">`CreateSubKey` Yöntemi `My.Computer.Registry` nesnesi, bir kayıt defteri anahtarı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab97e-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="ab97e-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="ab97e-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="ab97e-105">Bir kayıt defteri anahtarı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ab97e-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="ab97e-106">Kullanım `CreateSubKey` yöntemi, anahtarın adının yanı sıra anahtarı altındaki yerleştirmek için hangi hive belirtme.</span><span class="sxs-lookup"><span data-stu-id="ab97e-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="ab97e-107">Parametre `Subkey` büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="ab97e-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="ab97e-108">Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında.</span><span class="sxs-lookup"><span data-stu-id="ab97e-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="ab97e-109">Bir kayıt defteri anahtarı oluşturmak ve bunu bir değer ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ab97e-109">To create a registry key and set a value in it</span></span>  
  
1.  <span data-ttu-id="ab97e-110">Kullanım `CreateSubkey` yöntemi, anahtarın adının yanı sıra anahtarı altındaki yerleştirmek için hangi hive belirtme.</span><span class="sxs-lookup"><span data-stu-id="ab97e-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="ab97e-111">Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında.</span><span class="sxs-lookup"><span data-stu-id="ab97e-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  <span data-ttu-id="ab97e-112">Değeriyle ayarlamak `SetValue` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ab97e-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="ab97e-113">Bu örnekte, dize değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ab97e-113">This example sets the string value.</span></span> <span data-ttu-id="ab97e-114">"" Test değeri olan"için MyTestKeyValue".</span><span class="sxs-lookup"><span data-stu-id="ab97e-114">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="ab97e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab97e-115">Example</span></span>  
 <span data-ttu-id="ab97e-116">Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında ve dize değeri ayarlar `MyTestKeyValue` için `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="ab97e-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ab97e-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ab97e-117">Robust Programming</span></span>  
 <span data-ttu-id="ab97e-118">Anahtarınız için uygun bir konum bulmak için kayıt defteri yapısı inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ab97e-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="ab97e-119">Örneğin, geçerli kullanıcının HKEY_CURRENT_USER\Software anahtarını açın ve şirketinizin adı ile bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab97e-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="ab97e-120">Ardından, şirketinizin anahtarına kayıt defteri değerlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ab97e-120">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="ab97e-121">Kayıt defteri bir Web uygulamasından okurken, geçerli kullanıcının kimlik doğrulaması ve kimliğe bürünme Web uygulamasında uygulanan bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ab97e-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="ab97e-122">Kullanıcı klasörüne veri yazmak için daha güvenlidir (<xref:Microsoft.Win32.Registry.CurrentUser>) yerine yerel bilgisayarda (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="ab97e-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="ab97e-123">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab97e-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="ab97e-124">Başka bir işlem, belki de kötü amaçlı bir değer önceden oluşturduğunuz ve buna erişiminiz.</span><span class="sxs-lookup"><span data-stu-id="ab97e-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="ab97e-125">Kayıt defteri değerindeki veri geçirdiğinizde, verileri başka bir işlem mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ab97e-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="ab97e-126">Bunu önlemek için kullanmak <xref:Microsoft.Win32.RegistryKey.GetValue%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ab97e-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="ab97e-127">Döndürdüğü `Nothing` anahtarı zaten mevcut değilse.</span><span class="sxs-lookup"><span data-stu-id="ab97e-127">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="ab97e-128">Kayıt defteri anahtarı, ACL'ler tarafından (erişim denetim listeleri) korumalı olsa bile düz metin olarak kayıt defterinde parolalar gibi gizli depolamak için güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="ab97e-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="ab97e-129">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="ab97e-129">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ab97e-130">Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ab97e-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="ab97e-131">Kullanıcının kayıt defteri anahtarları oluşturma izni yok (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ab97e-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="ab97e-132">Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ab97e-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="ab97e-133">Anahtar kapalı (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ab97e-133">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="ab97e-134">Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="ab97e-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ab97e-135">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ab97e-135">.NET Framework Security</span></span>  
 <span data-ttu-id="ab97e-136">Bu işlem çalıştırmak için derleme ayrıcalık düzeyi verilen tarafından gerektiriyor <xref:System.Security.Permissions.RegistryPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ab97e-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="ab97e-137">Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="ab97e-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="ab97e-138">Benzer şekilde, kullanıcının oluşturulması veya ayarları için doğru ACL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab97e-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="ab97e-139">Örneğin, kod erişimi güvenlik izni olan yerel bir uygulama işletim sistemi izni olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ab97e-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="ab97e-140">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="ab97e-140">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab97e-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab97e-141">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>  
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>  
 [<span data-ttu-id="ab97e-142">Okuma ve kayıt defterine yazma</span><span class="sxs-lookup"><span data-stu-id="ab97e-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [<span data-ttu-id="ab97e-143">Kod erişim güvenliği temelleri</span><span class="sxs-lookup"><span data-stu-id="ab97e-143">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)
