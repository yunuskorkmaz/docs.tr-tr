---
title: 'Nasıl Yapılır: Kayıt Defteri Anahtarından Değer Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 73c32aefe06a68bb42fcb5f4615da0927e57e892
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345612"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="b5adb-102">Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarından Değer Okuma</span><span class="sxs-lookup"><span data-stu-id="b5adb-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>

<span data-ttu-id="b5adb-103">`My.Computer.Registry` Nesnenin `GetValue` yöntemi, Windows kayıt defterindeki değerleri okumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5adb-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="b5adb-104">Aşağıdaki örnekte yer alan "Software\MyApp" tuşu yoksa bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="b5adb-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="b5adb-105">Aşağıdaki `ValueName`örnekte "Ad" yoksa, `Nothing` döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b5adb-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="b5adb-106">Yöntem, `GetValue` belirli bir kayıt defteri anahtarında belirli bir değerin bulunup bulunmadığını belirlemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5adb-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="b5adb-107">Kod bir Web uygulamasından kayıt defterini okuduğunda, geçerli kullanıcı Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b5adb-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="b5adb-108">Kayıt defteri anahtarından bir değeri okumak için</span><span class="sxs-lookup"><span data-stu-id="b5adb-108">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="b5adb-109">Kayıt `GetValue` defteri anahtarından bir değer okumak için yolu ve adı belirterek yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5adb-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="b5adb-110">Aşağıdaki örnekteki değeri `Name` `HKEY_CURRENT_USER\Software\MyApp` okur ve bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b5adb-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="b5adb-111">Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5adb-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b5adb-112">Kod snippet picker, **Windows İşletim Sistemi > Kayıt Bulunmaktadır.**</span><span class="sxs-lookup"><span data-stu-id="b5adb-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="b5adb-113">Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.</span><span class="sxs-lookup"><span data-stu-id="b5adb-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="b5adb-114">Kayıt defteri anahtarında bir değerin bulunup bulunmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="b5adb-114">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="b5adb-115">Değeri `GetValue` almak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5adb-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="b5adb-116">Aşağıdaki kod, değerin var olup olmadığını denetler ve yoksa bir iletiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b5adb-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b5adb-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b5adb-117">Robust Programming</span></span>  

 <span data-ttu-id="b5adb-118">Kayıt defteri, verileri depolamak için kullanılan üst düzey veya kök anahtarlarını tutar.</span><span class="sxs-lookup"><span data-stu-id="b5adb-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="b5adb-119">Örneğin, HKEY_LOCAL_MACHINE kök anahtarı tüm kullanıcılar tarafından kullanılan makine düzeyindeayarları depolamak için kullanılırken, HKEY_CURRENT_USER tek bir kullanıcıya özgü verileri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b5adb-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="b5adb-120">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="b5adb-120">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b5adb-121">Anahtarın adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b5adb-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b5adb-122">Kullanıcının kayıt defteri anahtarlarından okuma izni<xref:System.Security.SecurityException>yoktur ( ).</span><span class="sxs-lookup"><span data-stu-id="b5adb-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="b5adb-123">Anahtar adı 255 karakter sınırını aşıyor<xref:System.ArgumentException>( ).</span><span class="sxs-lookup"><span data-stu-id="b5adb-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b5adb-124">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b5adb-124">.NET Framework Security</span></span>  

 <span data-ttu-id="b5adb-125">Bu işlemi çalıştırmak için derlemeniz <xref:System.Security.Permissions.RegistryPermission> sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b5adb-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="b5adb-126">Kısmi güven bağlamında çalışıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum atabilir.</span><span class="sxs-lookup"><span data-stu-id="b5adb-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="b5adb-127">Benzer şekilde, kullanıcının ayarlar oluşturmak veya yazmak için doğru ALA'lara sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5adb-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="b5adb-128">Örneğin, kod erişim güvenlik iznine sahip yerel bir uygulamanın işletim sistemi izni olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b5adb-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="b5adb-129">Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../../../../framework/misc/code-access-security-basics.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b5adb-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5adb-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5adb-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="b5adb-131">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="b5adb-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
