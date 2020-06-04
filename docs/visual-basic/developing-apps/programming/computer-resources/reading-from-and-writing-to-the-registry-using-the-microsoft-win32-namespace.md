---
title: Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 10431b1ad40ed320541a22fb46cc8db6dbb775b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360078"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="41879-102">Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41879-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="41879-103">, `My.Computer.Registry` Kayıt defterine karşı programlama yaparken temel ihtiyaçlarınızı kapsamalıdır, ancak <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> .NET Framework ad alanındaki ve sınıflarını da kullanabilirsiniz <xref:Microsoft.Win32> .</span><span class="sxs-lookup"><span data-stu-id="41879-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="41879-104">Kayıt defteri sınıfındaki anahtarlar</span><span class="sxs-lookup"><span data-stu-id="41879-104">Keys in the Registry Class</span></span>  

 <span data-ttu-id="41879-105"><xref:Microsoft.Win32.Registry>Sınıfı, alt anahtarlara ve değerlerine erişmek için kullanılabilen temel kayıt defteri anahtarlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="41879-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="41879-106">Temel anahtarlar salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="41879-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="41879-107">Aşağıdaki tabloda, sınıfının açığa çıkarılan yedi anahtar listelenmektedir ve açıklanmaktadır <xref:Microsoft.Win32.Registry> .</span><span class="sxs-lookup"><span data-stu-id="41879-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="41879-108">**Anahtar**</span><span class="sxs-lookup"><span data-stu-id="41879-108">**Key**</span></span>|<span data-ttu-id="41879-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="41879-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="41879-110">Belge türlerini ve bu türlerle ilişkili özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="41879-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="41879-111">Kullanıcıya özgü olmayan donanım yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="41879-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="41879-112">Ortam değişkenleri gibi geçerli kullanıcı tercihleri hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="41879-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="41879-113">Sanal cihaz sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="41879-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="41879-114">Yerel bilgisayar için yapılandırma verilerini tutan beş alt anahtar (donanım, SAM, güvenlik, yazılım ve sistem) içerir.</span><span class="sxs-lookup"><span data-stu-id="41879-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="41879-115">Yazılım bileşenleri için performans bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="41879-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="41879-116">Varsayılan Kullanıcı tercihleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="41879-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="41879-117">Geçerli kullanıcıya () yerel bilgisayardan () veri yazmak daha güvenlidir <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.Registry.LocalMachine> .</span><span class="sxs-lookup"><span data-stu-id="41879-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="41879-118">Oluşturmakta olduğunuz anahtar daha önce başka bir kötü amaçlı, büyük olasılıkla kötü amaçlı bir işlem tarafından oluşturulduğu zaman, genellikle "ele geçirme" olarak adlandırılan bir koşul oluşur.</span><span class="sxs-lookup"><span data-stu-id="41879-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="41879-119">Bunun oluşmasını önlemek için, <xref:Microsoft.Win32.RegistryKey.GetValue%2A> anahtar zaten yoksa, gibi bir yöntemi kullanın `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="41879-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="41879-120">Kayıt defterinden bir değer okuma</span><span class="sxs-lookup"><span data-stu-id="41879-120">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="41879-121">Aşağıdaki kod, HKEY_CURRENT_USER bir dizenin nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="41879-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="41879-122">Aşağıdaki kod, HKEY_CURRENT_USER için bir dize okur, artırır ve yazar.</span><span class="sxs-lookup"><span data-stu-id="41879-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="41879-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41879-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="41879-124">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="41879-124">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="41879-125">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="41879-125">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="41879-126">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="41879-126">Security and the Registry</span></span>](security-and-the-registry.md)
