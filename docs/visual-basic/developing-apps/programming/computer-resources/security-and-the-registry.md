---
title: Güvenlik ve Kayıt Defteri
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 2eba9d177769b22de3f931bc7af4905a80e316b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359974"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="6b35f-102">Güvenlik ve Kayıt Defteri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b35f-102">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="6b35f-103">Bu sayfada, verileri kayıt defterine depolamanın güvenlik etkileri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b35f-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="6b35f-104">İzinler</span><span class="sxs-lookup"><span data-stu-id="6b35f-104">Permissions</span></span>  

 <span data-ttu-id="6b35f-105">Kayıt defteri anahtarı ACL 'Ler (erişim denetim listeleri) tarafından korunsa bile, parolalar gibi gizli dizileri, kayıt defterindeki düz metin olarak depolamak güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="6b35f-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="6b35f-106">Kayıt defteriyle çalışma, sistem kaynaklarına veya korunan bilgilere uygunsuz erişime izin vererek güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="6b35f-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="6b35f-107">Bu özellikleri kullanmak için, Numaralandırmadaki okuma ve yazma izinlerine sahip olmanız gerekir ve bu <xref:System.Security.Permissions.RegistryPermissionAccess> , kayıt defteri değişkenlerine erişimi denetler.</span><span class="sxs-lookup"><span data-stu-id="6b35f-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="6b35f-108">Tam güvenle çalışan tüm kodlar (varsayılan güvenlik ilkesi altında, kullanıcının yerel sabit diskinde yüklü olan tüm kodlar), kayıt defterine erişmek için gerekli izinlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6b35f-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="6b35f-109">Daha fazla bilgi için bkz <xref:System.Security.Permissions.RegistryPermission> . sınıf.</span><span class="sxs-lookup"><span data-stu-id="6b35f-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="6b35f-110">Kayıt defteri değişkenleri, kodun hiçbir şekilde erişebileceği bellek konumlarında depolanmamalıdır <xref:System.Security.Permissions.RegistryPermission> .</span><span class="sxs-lookup"><span data-stu-id="6b35f-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="6b35f-111">Benzer şekilde, izin verirken işi almak için gereken en düşük ayrıcalıklara izin verin.</span><span class="sxs-lookup"><span data-stu-id="6b35f-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="6b35f-112">Kayıt defteri izin erişim değerleri Listeleme tarafından tanımlanır <xref:System.Security.Permissions.RegistryPermissionAccess> .</span><span class="sxs-lookup"><span data-stu-id="6b35f-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="6b35f-113">Aşağıdaki tabloda üyelerinin ayrıntıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b35f-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="6b35f-114">Değer</span><span class="sxs-lookup"><span data-stu-id="6b35f-114">Value</span></span>|<span data-ttu-id="6b35f-115">Kayıt defteri değişkenlerine erişim</span><span class="sxs-lookup"><span data-stu-id="6b35f-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="6b35f-116">Oluşturma, okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="6b35f-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="6b35f-117">Oluştur</span><span class="sxs-lookup"><span data-stu-id="6b35f-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="6b35f-118">Erişim yok</span><span class="sxs-lookup"><span data-stu-id="6b35f-118">No access</span></span>|  
|`Read`|<span data-ttu-id="6b35f-119">Okuma</span><span class="sxs-lookup"><span data-stu-id="6b35f-119">Read</span></span>|  
|`Write`|<span data-ttu-id="6b35f-120">Yazma</span><span class="sxs-lookup"><span data-stu-id="6b35f-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="6b35f-121">Kayıt defteri anahtarlarındaki değerler denetleniyor</span><span class="sxs-lookup"><span data-stu-id="6b35f-121">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="6b35f-122">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b35f-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="6b35f-123">Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b35f-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="6b35f-124">Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b35f-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="6b35f-125">Bunu engellemek için `GetValue` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6b35f-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="6b35f-126">`Nothing`Anahtar zaten mevcut değilse döndürür.</span><span class="sxs-lookup"><span data-stu-id="6b35f-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6b35f-127">Bir Web uygulamasından kayıt defteri okunurken geçerli kullanıcının kimliği, Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme özelliğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6b35f-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b35f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b35f-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="6b35f-129">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="6b35f-129">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
