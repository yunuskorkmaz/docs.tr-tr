---
title: Güvenlik ve Kayıt Defteri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: dc0071d1fddf99bd712ebe8aea5c61bbc3522f93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839364"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="94a0d-102">Güvenlik ve Kayıt Defteri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94a0d-102">Security and the Registry (Visual Basic)</span></span>
<span data-ttu-id="94a0d-103">Bu sayfa verileri kayıt defterinde depolama güvenlikle ilgili etkileri anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94a0d-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="94a0d-104">İzinler</span><span class="sxs-lookup"><span data-stu-id="94a0d-104">Permissions</span></span>  
 <span data-ttu-id="94a0d-105">Kayıt defteri anahtarı ACL (erişim denetim listeleri) tarafından korunuyor olsa bile kayıt defterinde düz metin parolalar gibi gizli dizileri depolamak için güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="94a0d-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="94a0d-106">Kayıt defteri ile çalışma, sistem kaynakları için uygun olmayan erişimine izin vererek güvenliği tehlikeye atabilir veya korumalı bilgileri.</span><span class="sxs-lookup"><span data-stu-id="94a0d-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="94a0d-107">Bu özellikleri kullanmak için olmalıdır okuma ve Yazma izinlerinden <xref:System.Security.Permissions.RegistryPermissionAccess> kayıt defteri değişkenlerine erişimi denetleyen sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="94a0d-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="94a0d-108">Tam güven ile çalışan herhangi bir kod (varsayılan güvenlik ilkesini altında kullanıcının yerel sabit diskinde yüklü herhangi bir kod budur) kayıt defterine erişim için gerekli izinlere sahip.</span><span class="sxs-lookup"><span data-stu-id="94a0d-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="94a0d-109">Daha fazla bilgi için <xref:System.Security.Permissions.RegistryPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="94a0d-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="94a0d-110">Kayıt defteri değişkenleri bellek konumlarda olmayan depolanmalıdır burada olmadan kod <xref:System.Security.Permissions.RegistryPermission> erişebilir.</span><span class="sxs-lookup"><span data-stu-id="94a0d-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="94a0d-111">Benzer şekilde, izin verirken, işin tamamlanması için gereken en düşük ayrıcalıkları verin.</span><span class="sxs-lookup"><span data-stu-id="94a0d-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="94a0d-112">Kayıt defteri izni erişim değerleri tarafından tanımlanan <xref:System.Security.Permissions.RegistryPermissionAccess> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="94a0d-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="94a0d-113">Aşağıdaki tabloda üyelerini ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="94a0d-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="94a0d-114">Değer</span><span class="sxs-lookup"><span data-stu-id="94a0d-114">Value</span></span>|<span data-ttu-id="94a0d-115">Kayıt defteri değişkenlerine erişimi</span><span class="sxs-lookup"><span data-stu-id="94a0d-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="94a0d-116">Oluşturun, okuyun ve yazma</span><span class="sxs-lookup"><span data-stu-id="94a0d-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="94a0d-117">Create</span><span class="sxs-lookup"><span data-stu-id="94a0d-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="94a0d-118">Erişim yok</span><span class="sxs-lookup"><span data-stu-id="94a0d-118">No access</span></span>|  
|`Read`|<span data-ttu-id="94a0d-119">Oku</span><span class="sxs-lookup"><span data-stu-id="94a0d-119">Read</span></span>|  
|`Write`|<span data-ttu-id="94a0d-120">Write</span><span class="sxs-lookup"><span data-stu-id="94a0d-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="94a0d-121">Kayıt defteri anahtarlarını değerleri denetleniyor</span><span class="sxs-lookup"><span data-stu-id="94a0d-121">Checking Values in Registry Keys</span></span>  
 <span data-ttu-id="94a0d-122">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="94a0d-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="94a0d-123">Başka bir işlem, belki de kötü amaçlı bir değeri önceden oluşturmuş olabilir ve erişmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94a0d-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="94a0d-124">Kayıt defteri değerine veri koyduğunuzda, veriler başka bir işlem için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94a0d-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="94a0d-125">Bunu önlemek için `GetValue` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="94a0d-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="94a0d-126">Döndürür `Nothing` anahtarı zaten mevcut değilse.</span><span class="sxs-lookup"><span data-stu-id="94a0d-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94a0d-127">Kayıt defterinde bir Web uygulamasından okurken, geçerli kullanıcının kimliğini kimlik doğrulama ve Web uygulamasında gerçekleştirilen kimliğe bürünme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="94a0d-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a0d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94a0d-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="94a0d-129">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="94a0d-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
