---
title: "Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarından Değer Okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f88401f6daa7a2108522496c845521474c22cc30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="9e8d6-102">Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarından Değer Okuma</span><span class="sxs-lookup"><span data-stu-id="9e8d6-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>
<span data-ttu-id="9e8d6-103">`GetValue` Yöntemi `My.Computer.Registry` nesnesi, Windows kayıt defteri değerlerini okumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="9e8d6-104">Aşağıdaki örnekte, "Software\MyApp" anahtar mevcut değilse özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="9e8d6-105">Varsa `ValueName`, "Adı" aşağıdaki örnekte, mevcut olmadığından `Nothing` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="9e8d6-106">`GetValue` Yöntemi de belirli bir değeri bir kayıt defteri anahtarı var olup olmadığını belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="9e8d6-107">Kod bir Web uygulamasından kayıt okuduğunda, geçerli kullanıcının kimlik doğrulaması ve Web uygulamasında uygulanan kimliğe bürünme tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="9e8d6-108">Kayıt defteri anahtarından değer okuma için</span><span class="sxs-lookup"><span data-stu-id="9e8d6-108">To read a value from a registry key</span></span>  
  
-   <span data-ttu-id="9e8d6-109">Kullanmak `GetValue` yöntemi, adını ve yolunu belirtme) kayıt defteri anahtarından değer okuma için.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="9e8d6-110">Aşağıdaki örnek değeri okuyan `Name` gelen `HKEY_CURRENT_USER\Software\MyApp` ve bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 <span data-ttu-id="9e8d6-111">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="9e8d6-112">Kod parçacığı Seçici bulunur **Windows işletim sistemi > kayıt defteri**.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="9e8d6-113">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="9e8d6-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="9e8d6-114">Bir değer olup olmadığını belirlemek için bir kayıt defteri anahtarı var</span><span class="sxs-lookup"><span data-stu-id="9e8d6-114">To determine whether a value exists in a registry key</span></span>  
  
-   <span data-ttu-id="9e8d6-115">Kullanım `GetValue` değerini almak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="9e8d6-116">Aşağıdaki kod, değer var ve mevcut değilse bir ileti döndürür denetler.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9e8d6-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="9e8d6-117">Robust Programming</span></span>  
 <span data-ttu-id="9e8d6-118">Kayıt defteri en üst düzey tutan veya kök, verileri depolamak için kullanılan anahtarları.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="9e8d6-119">Örneğin, HKEY_LOCAL_MACHINE kök anahtarı HKEY_CURRENT_USER tek bir kullanıcıya özgü verileri depolamak için kullanılırken, tüm kullanıcılar tarafından kullanılan makine düzeyi ayarlarını depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="9e8d6-120">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="9e8d6-120">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9e8d6-121">Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="9e8d6-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="9e8d6-122">Kullanıcının kayıt defteri anahtarları okuma izni yok (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9e8d6-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="9e8d6-123">Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="9e8d6-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9e8d6-124">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9e8d6-124">.NET Framework Security</span></span>  
 <span data-ttu-id="9e8d6-125">Bu işlem çalıştırmak için derleme ayrıcalık düzeyi verilen tarafından gerektiriyor <xref:System.Security.Permissions.RegistryPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="9e8d6-126">Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="9e8d6-127">Benzer şekilde, kullanıcının oluşturulması veya ayarları için doğru ACL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="9e8d6-128">Örneğin, kod erişimi güvenlik izni olan yerel bir uygulama işletim sistemi izni olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="9e8d6-129">Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](https://msdn.microsoft.com/library/33tceax8).</span><span class="sxs-lookup"><span data-stu-id="9e8d6-129">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e8d6-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e8d6-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [<span data-ttu-id="9e8d6-131">Okuma ve kayıt defterine yazma</span><span class="sxs-lookup"><span data-stu-id="9e8d6-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
