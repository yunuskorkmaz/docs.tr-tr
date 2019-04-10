---
title: "Nasıl yapılır: Bir kayıt defteri anahtarı oluşturun ve Visual Basic'te değerini ayarlama"
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
ms.openlocfilehash: 0cadff8b44c60041e2664b1d3b70830209014301
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312625"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="03105-102">Nasıl yapılır: Bir kayıt defteri anahtarı oluşturun ve Visual Basic'te değerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="03105-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="03105-103">`CreateSubKey` Yöntemi `My.Computer.Registry` nesnesi, bir kayıt defteri anahtarı oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03105-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="03105-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="03105-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="03105-105">Bir kayıt defteri anahtarı oluşturma</span><span class="sxs-lookup"><span data-stu-id="03105-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="03105-106">Kullanım `CreateSubKey` , anahtarın adını yanı sıra anahtarı altındaki yerleştirmek için hive'ı belirtme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03105-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="03105-107">Parametre `Subkey` büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="03105-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="03105-108">Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında.</span><span class="sxs-lookup"><span data-stu-id="03105-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="03105-109">Bir kayıt defteri anahtarı oluşturun ve içinde bir değer ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="03105-109">To create a registry key and set a value in it</span></span>  
  
1. <span data-ttu-id="03105-110">Kullanım `CreateSubkey` , anahtarın adını yanı sıra anahtarı altındaki yerleştirmek için hive'ı belirtme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03105-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="03105-111">Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında.</span><span class="sxs-lookup"><span data-stu-id="03105-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
2. <span data-ttu-id="03105-112">Değer `SetValue` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03105-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="03105-113">Bu örnekte, dize değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="03105-113">This example sets the string value.</span></span> <span data-ttu-id="03105-114">"" Test değeri olan"için MyTestKeyValue".</span><span class="sxs-lookup"><span data-stu-id="03105-114">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="03105-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="03105-115">Example</span></span>  
 <span data-ttu-id="03105-116">Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında ve sonra da dize değeri ayarlar `MyTestKeyValue` için `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="03105-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 [!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]  
  
## <a name="robust-programming"></a><span data-ttu-id="03105-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="03105-117">Robust Programming</span></span>  
 <span data-ttu-id="03105-118">Anahtarınız için uygun bir konum bulmak üzere kayıt yapısını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="03105-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="03105-119">Örneğin, geçerli kullanıcının HKEY_CURRENT_USER\Software anahtarı açın ve şirketinizin adıyla bir anahtar oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03105-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="03105-120">Ardından kayıt defteri değerlerini şirketinizin anahtarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="03105-120">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="03105-121">Kayıt defterinde bir Web uygulamasından okurken, geçerli kullanıcının kimlik doğrulaması ve Web uygulamasında gerçekleştirilen kimliğe bürünme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="03105-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="03105-122">Verilerin kullanıcı klasörüne yazılması daha güvenlidir (<xref:Microsoft.Win32.Registry.CurrentUser>) yerine yerel bilgisayarda (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="03105-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="03105-123">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="03105-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="03105-124">Başka bir işlem, belki de kötü amaçlı bir değeri önceden oluşturmuş olabilir ve erişmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03105-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="03105-125">Kayıt defteri değerine veri koyduğunuzda, veriler başka bir işlem için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03105-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="03105-126">Bunu önlemek için <xref:Microsoft.Win32.RegistryKey.GetValue%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03105-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="03105-127">Döndürür `Nothing` anahtarı zaten mevcut değilse.</span><span class="sxs-lookup"><span data-stu-id="03105-127">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="03105-128">Kayıt defteri anahtarı, ACL'ler tarafından (erişim denetim listeleri) korunuyor olsa bile kayıt defterinde düz metin parolalar gibi gizli dizileri depolamak için güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="03105-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="03105-129">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="03105-129">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="03105-130">Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="03105-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="03105-131">Kullanıcının kayıt defteri anahtarlarını oluşturma izni yok (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="03105-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="03105-132">Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="03105-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="03105-133">Anahtar kapalı (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="03105-133">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="03105-134">Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="03105-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="03105-135">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="03105-135">.NET Framework Security</span></span>  
 <span data-ttu-id="03105-136">Bu işlemi çalıştırmak için ayrıcalık düzeyi verilen tarafından derlemeyi <xref:System.Security.Permissions.RegistryPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="03105-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="03105-137">Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="03105-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="03105-138">Benzer şekilde, kullanıcı oluşturma veya ayarlarına yazma için doğru ACL'leri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="03105-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="03105-139">Örneğin, kod erişim güvenlik izni olan yerel bir uygulama işletim sistemi izniniz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="03105-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="03105-140">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="03105-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03105-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03105-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="03105-142">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="03105-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="03105-143">Kod Erişim Güvenliği Temelleri</span><span class="sxs-lookup"><span data-stu-id="03105-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
