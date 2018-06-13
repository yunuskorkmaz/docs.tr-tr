---
title: Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 6309f312ed05f48e65b19d8827322071cad1f6de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588875"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="1585f-102">Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1585f-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="1585f-103">Ancak `My.Computer.Registry` temel gereksinimlerinizi kayıt defteri karşı programlama zaman kapsaması gereken, aynı zamanda <xref:Microsoft.Win32.Registry> ve <xref:Microsoft.Win32.RegistryKey> sınıfları <xref:Microsoft.Win32> ad alanı [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1585f-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="1585f-104">Kayıt defteri sınıfı anahtarları</span><span class="sxs-lookup"><span data-stu-id="1585f-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="1585f-105"><xref:Microsoft.Win32.Registry> Sınıfı alt anahtarları ve değerleri erişmek için kullanılan temel kayıt defteri anahtarlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1585f-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="1585f-106">Temel anahtarları salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="1585f-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="1585f-107">Aşağıdaki tabloda listelenmekte ve tarafından sunulan yedi anahtarları açıklanmaktadır <xref:Microsoft.Win32.Registry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1585f-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="1585f-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="1585f-108">**Key**</span></span>|<span data-ttu-id="1585f-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="1585f-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="1585f-110">Belgeler ve bu türleriyle ilişkili özellikleri türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1585f-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="1585f-111">Kullanıcıya özgü olmayan donanım yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1585f-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="1585f-112">Geçerli kullanıcı tercihleri gibi ortam değişkenleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1585f-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="1585f-113">Sanal cihaz sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1585f-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="1585f-114">Yerel bilgisayar için yapılandırma verilerini tutan beş alt anahtarları (donanım, SAM, güvenlik, yazılım ve sistem) içerir.</span><span class="sxs-lookup"><span data-stu-id="1585f-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="1585f-115">Yazılım bileşenleri için performans bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1585f-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="1585f-116">Varsayılan kullanıcı tercihleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1585f-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="1585f-117">Geçerli kullanıcının veri yazmak için daha güvenlidir (<xref:Microsoft.Win32.Registry.CurrentUser>) daha yerel bilgisayarda (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="1585f-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="1585f-118">Anahtar, oluştururken "ele geçirme" gerçekleştiği sırada, genellikle başvurulan bir koşul, daha önce başka bir, büyük olasılıkla kötü amaçlı işlem tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="1585f-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="1585f-119">Bu oluşmasını önlemek için bir yöntem gibi kullanın <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, döndüren `Nothing` anahtarı zaten mevcut değilse.</span><span class="sxs-lookup"><span data-stu-id="1585f-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="1585f-120">Kayıt defteri anahtarından değer okuma</span><span class="sxs-lookup"><span data-stu-id="1585f-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="1585f-121">Aşağıdaki kod, bir dize HKEY_CURRENT_USER okuma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1585f-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 <span data-ttu-id="1585f-122">Aşağıdaki kod, artışlarla okur ve ardından bir dize HKEY_CURRENT_USER yazar.</span><span class="sxs-lookup"><span data-stu-id="1585f-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1585f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1585f-123">See Also</span></span>  
 <xref:System.SystemException>  
 <xref:System.ApplicationException>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [<span data-ttu-id="1585f-124">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="1585f-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="1585f-125">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="1585f-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [<span data-ttu-id="1585f-126">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="1585f-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
