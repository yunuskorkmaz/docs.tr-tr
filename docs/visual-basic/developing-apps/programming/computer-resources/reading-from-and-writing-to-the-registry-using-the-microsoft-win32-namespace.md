---
title: Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345492"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="4b3c4-102">Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b3c4-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="4b3c4-103">Kayıt `My.Computer.Registry` defterine karşı programlama yaparken temel gereksinimlerinizi karşılamanız <xref:Microsoft.Win32.Registry> gerekse <xref:Microsoft.Win32> de, .NET Framework'ün ad alanında ve <xref:Microsoft.Win32.RegistryKey> sınıfları da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="4b3c4-104">Kayıt Defteri Sınıfındaki Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="4b3c4-104">Keys in the Registry Class</span></span>  

 <span data-ttu-id="4b3c4-105">Sınıf, <xref:Microsoft.Win32.Registry> alt anahtarlara ve değerlerine erişmek için kullanılabilecek temel kayıt defteri anahtarlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="4b3c4-106">Temel anahtarların kendileri salt okunur.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="4b3c4-107">Aşağıdaki tablo listeler ve <xref:Microsoft.Win32.Registry> sınıf tarafından maruz yedi tuşları açıklar.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="4b3c4-108">**Anahtar**</span><span class="sxs-lookup"><span data-stu-id="4b3c4-108">**Key**</span></span>|<span data-ttu-id="4b3c4-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="4b3c4-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="4b3c4-110">Belge türlerini ve bu türlerle ilişkili özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="4b3c4-111">Kullanıcıya özel olmayan donanım yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="4b3c4-112">Çevresel değişkenler gibi geçerli kullanıcı tercihleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="4b3c4-113">Sanal Aygıt Sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="4b3c4-114">Yerel bilgisayarın yapılandırma verilerini tutan beş alt anahtar (Donanım, SAM, Güvenlik, Yazılım ve Sistem) içerir.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="4b3c4-115">Yazılım bileşenleri için performans bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="4b3c4-116">Varsayılan kullanıcı tercihleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="4b3c4-117">Yerel bilgisayara ()<xref:Microsoft.Win32.Registry.CurrentUser>veri yazmak, () mevcut kullanıcıya yazmak daha güvenlidir.<xref:Microsoft.Win32.Registry.LocalMachine></span><span class="sxs-lookup"><span data-stu-id="4b3c4-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="4b3c4-118">Genellikle "çömelme" olarak adlandırılan bir koşul, oluşturduğunuz anahtar daha önce başka bir kötü amaçlı işlem tarafından oluşturulduğunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="4b3c4-119">Bunun oluşmasını önlemek için, anahtar <xref:Microsoft.Win32.RegistryKey.GetValue%2A>zaten yoksa `Nothing` döndüren bir yöntem kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="4b3c4-120">Kayıt Defterinden Değer Okuma</span><span class="sxs-lookup"><span data-stu-id="4b3c4-120">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="4b3c4-121">Aşağıdaki kod, HKEY_CURRENT_USER bir dizenasıl okunduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="4b3c4-122">Aşağıdaki kod okur, artışlar ve sonra HKEY_CURRENT_USER için bir dize yazar.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="4b3c4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b3c4-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="4b3c4-124">Deneyin... Yakalamak... Son İfade</span><span class="sxs-lookup"><span data-stu-id="4b3c4-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="4b3c4-125">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="4b3c4-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="4b3c4-126">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="4b3c4-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
