---
title: Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: f958fe9355e8c4e3701996cb33e48bd3e2bd759f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921296"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="81280-102">Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81280-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="81280-103">Ancak `My.Computer.Registry` gereksinimlerinizi temel kayıt defteri karşı programlama yaparken kapsamalıdır, ayrıca <xref:Microsoft.Win32.Registry> ve <xref:Microsoft.Win32.RegistryKey> sınıfları <xref:Microsoft.Win32> ad [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81280-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="81280-104">Kayıt defteri sınıfı anahtarları</span><span class="sxs-lookup"><span data-stu-id="81280-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="81280-105"><xref:Microsoft.Win32.Registry> Sınıfı alt anahtarları ve değerlerini erişmek için kullanılan temel kayıt defteri anahtarlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="81280-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="81280-106">Temel anahtarları salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="81280-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="81280-107">Aşağıdaki tabloda listelenmiş ve açıklar tarafından kullanıma sunulan yedi anahtarları <xref:Microsoft.Win32.Registry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="81280-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="81280-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="81280-108">**Key**</span></span>|<span data-ttu-id="81280-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="81280-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="81280-110">Belgeler ve bu türleriyle ilişkili özellikleri türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81280-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="81280-111">Kullanıcıya özgü olmayan donanım yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="81280-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="81280-112">Geçerli kullanıcı tercihleri gibi ortam değişkenleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="81280-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="81280-113">Sanal cihaz sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="81280-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="81280-114">Yerel bilgisayar için yapılandırma verilerini tutun beş alt (donanım, SAM, güvenlik, yazılım ve sistem) içerir.</span><span class="sxs-lookup"><span data-stu-id="81280-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="81280-115">Yazılım bileşenlerinin performans bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="81280-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="81280-116">Varsayılan kullanıcı tercihlerini hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="81280-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="81280-117">Geçerli kullanıcıya veri yazmak için daha güvenlidir (<xref:Microsoft.Win32.Registry.CurrentUser>) değerinden yerel bilgisayarda (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="81280-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="81280-118">Anahtar, oluştururken "ele geçirme" gerçekleştiği sırada genellikle adlandırılır bir koşul, daha önce başka bir, büyük olasılıkla kötü amaçlı işlemi tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="81280-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="81280-119">Bunun gerçekleşmesini önlemek için bir yöntem gibi kullanın <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, döndüren `Nothing` anahtarı zaten mevcut değilse.</span><span class="sxs-lookup"><span data-stu-id="81280-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="81280-120">Bir değeri Kayıt Defteri'nden okuma</span><span class="sxs-lookup"><span data-stu-id="81280-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="81280-121">Aşağıdaki kod, bir dize HKEY_CURRENT_USER okumak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="81280-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="81280-122">Aşağıdaki kod, artışlarla okur ve sonra bir dize HKEY_CURRENT_USER üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="81280-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="81280-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81280-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="81280-124">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="81280-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="81280-125">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="81280-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="81280-126">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="81280-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
