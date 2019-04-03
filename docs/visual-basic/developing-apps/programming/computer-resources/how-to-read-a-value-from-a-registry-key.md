---
title: "Nasıl yapılır: Visual Basic'te kayıt defteri anahtarından değer okuma"
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: bc71dd2e3a78454236b2f6f30c2d51aa596e5b8c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840191"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="03251-102">Nasıl yapılır: Visual Basic'te kayıt defteri anahtarından değer okuma</span><span class="sxs-lookup"><span data-stu-id="03251-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>
<span data-ttu-id="03251-103">`GetValue` Yöntemi `My.Computer.Registry` nesne, Windows kayıt defteri değerlerini okumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03251-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="03251-104">Aşağıdaki örnekte, "Software\MyApp" anahtar mevcut değilse bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="03251-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="03251-105">Varsa `ValueName`, "Name" aşağıdaki örnekte, mevcut değil, `Nothing` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="03251-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="03251-106">`GetValue` Yöntemi de belirli bir değeri belirli kayıt defteri anahtarında var olup olmadığını belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03251-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="03251-107">Kodu bir Web uygulamasından kayıt defteri okuduğunda, geçerli kullanıcının kimlik doğrulaması ve Web uygulamasında gerçekleştirilen kimliğe bürünme tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="03251-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="03251-108">Kayıt defteri anahtarından değer okuma için</span><span class="sxs-lookup"><span data-stu-id="03251-108">To read a value from a registry key</span></span>  
  
-   <span data-ttu-id="03251-109">Kullanma `GetValue` yolunu ve adını belirterek yöntemi) kayıt defteri anahtarından değer okuma için.</span><span class="sxs-lookup"><span data-stu-id="03251-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="03251-110">Aşağıdaki örnek değeri okuyan `Name` gelen `HKEY_CURRENT_USER\Software\MyApp` ve bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="03251-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="03251-111">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03251-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="03251-112">Kod parçacığı Seçici'de bulunur **Windows işletim sistemi > kayıt defteri**.</span><span class="sxs-lookup"><span data-stu-id="03251-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="03251-113">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="03251-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="03251-114">Bir değer olup olmadığını belirlemek için bir kayıt defteri anahtarında var.</span><span class="sxs-lookup"><span data-stu-id="03251-114">To determine whether a value exists in a registry key</span></span>  
  
-   <span data-ttu-id="03251-115">Kullanım `GetValue` değerini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03251-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="03251-116">Aşağıdaki kod, değeri var ve bir ileti döndürür, aksi takdirde denetler.</span><span class="sxs-lookup"><span data-stu-id="03251-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="03251-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="03251-117">Robust Programming</span></span>  
 <span data-ttu-id="03251-118">Kayıt defteri, üst düzey tutan veya kök, verileri depolamak için kullanılan anahtarları.</span><span class="sxs-lookup"><span data-stu-id="03251-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="03251-119">Örneğin, HKEY_LOCAL_MACHINE kök anahtarı kullanılırken HKEY_CURRENT_USER tek bir kullanıcıya özgü verileri depolamak için tüm kullanıcılar tarafından kullanılan makine düzeyinde ayarlarını depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03251-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="03251-120">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="03251-120">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="03251-121">Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="03251-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="03251-122">Kullanıcı kayıt defteri anahtarlarını Okuma izinlerine sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="03251-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="03251-123">Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="03251-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="03251-124">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="03251-124">.NET Framework Security</span></span>  
 <span data-ttu-id="03251-125">Bu işlemi çalıştırmak için ayrıcalık düzeyi verilen tarafından derlemeyi <xref:System.Security.Permissions.RegistryPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="03251-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="03251-126">Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum fırlatabilir.</span><span class="sxs-lookup"><span data-stu-id="03251-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="03251-127">Benzer şekilde, kullanıcı oluşturma veya ayarlarına yazma için doğru ACL'leri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="03251-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="03251-128">Örneğin, kod erişim güvenlik izni olan yerel bir uygulama işletim sistemi izniniz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="03251-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="03251-129">Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="03251-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03251-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03251-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="03251-131">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="03251-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
