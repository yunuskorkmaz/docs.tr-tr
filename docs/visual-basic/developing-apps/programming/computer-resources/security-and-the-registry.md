---
title: Güvenlik ve Kayıt Defteri
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345478"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="abadb-102">Güvenlik ve Kayıt Defteri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abadb-102">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="abadb-103">Bu sayfada, kayıt defterinde veri depolamanın güvenlik sonuçları anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="abadb-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="abadb-104">İzinler</span><span class="sxs-lookup"><span data-stu-id="abadb-104">Permissions</span></span>  

 <span data-ttu-id="abadb-105">Kayıt defteri anahtarı ALA'lar (erişim denetim listeleri) tarafından korunsa bile, parolalar gibi sırları kayıt defterinde düz metin olarak depolamak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="abadb-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="abadb-106">Kayıt defteriyle çalışmak, sistem kaynaklarına veya korunan bilgilere uygunsuz erişime izin vererek güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="abadb-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="abadb-107">Bu özellikleri kullanmak için, kayıt defteri değişkenlerine <xref:System.Security.Permissions.RegistryPermissionAccess> erişimi denetleyen numaralandırmadan izinleri okuma ve yazma nız gerekir.</span><span class="sxs-lookup"><span data-stu-id="abadb-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="abadb-108">Tam güvenle çalışan herhangi bir kod (varsayılan güvenlik ilkesi altında, bu kullanıcının yerel sabit diskine yüklenen herhangi bir koddur) kayıt defterine erişmek için gerekli izinlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="abadb-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="abadb-109">Daha fazla bilgi <xref:System.Security.Permissions.RegistryPermission> için sınıfa bakın.</span><span class="sxs-lookup"><span data-stu-id="abadb-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="abadb-110">Kayıt defteri değişkenleri, kodun <xref:System.Security.Permissions.RegistryPermission> erişilebileceği bellek konumlarında depolanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="abadb-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="abadb-111">Benzer şekilde, izin verirken, işi yapmak için gereken minimum ayrıcalıkları tanıyın.</span><span class="sxs-lookup"><span data-stu-id="abadb-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="abadb-112">Kayıt defteri izni erişim değerleri <xref:System.Security.Permissions.RegistryPermissionAccess> numaralandırma ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="abadb-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="abadb-113">Aşağıdaki tablo üyeleri ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="abadb-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="abadb-114">Değer</span><span class="sxs-lookup"><span data-stu-id="abadb-114">Value</span></span>|<span data-ttu-id="abadb-115">Kayıt Defteri Değişkenlerine Erişim</span><span class="sxs-lookup"><span data-stu-id="abadb-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="abadb-116">Oluşturma, okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="abadb-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="abadb-117">Oluşturma</span><span class="sxs-lookup"><span data-stu-id="abadb-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="abadb-118">Erişim yok</span><span class="sxs-lookup"><span data-stu-id="abadb-118">No access</span></span>|  
|`Read`|<span data-ttu-id="abadb-119">Okuma</span><span class="sxs-lookup"><span data-stu-id="abadb-119">Read</span></span>|  
|`Write`|<span data-ttu-id="abadb-120">Yazma</span><span class="sxs-lookup"><span data-stu-id="abadb-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="abadb-121">Kayıt Defteri Anahtarlarında Değerleri Denetleme</span><span class="sxs-lookup"><span data-stu-id="abadb-121">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="abadb-122">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapacağınız gerektiğine karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="abadb-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="abadb-123">Başka bir işlem, belki de kötü niyetli bir, zaten değer yarattı ve ona erişimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="abadb-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="abadb-124">Verileri kayıt defteri değerine koyduğunuzda, veriler diğer işlem için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="abadb-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="abadb-125">Bunu önlemek için `GetValue` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="abadb-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="abadb-126">Anahtar `Nothing` zaten yoksa döndürür.</span><span class="sxs-lookup"><span data-stu-id="abadb-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="abadb-127">Bir Web uygulamasından kayıt defterini okurken, geçerli kullanıcının kimliği Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="abadb-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abadb-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abadb-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="abadb-129">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="abadb-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
