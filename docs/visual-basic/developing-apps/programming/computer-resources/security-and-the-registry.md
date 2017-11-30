---
title: "Güvenlik ve Kayıt Defteri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0961d21417cbb5efcd9f38112c4e8ecb393faccd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="48a59-102">Güvenlik ve Kayıt Defteri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a59-102">Security and the Registry (Visual Basic)</span></span>
<span data-ttu-id="48a59-103">Bu sayfa verileri kayıt defterinde depolama güvenlik etkilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="48a59-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="48a59-104">İzinler</span><span class="sxs-lookup"><span data-stu-id="48a59-104">Permissions</span></span>  
 <span data-ttu-id="48a59-105">Kayıt defteri anahtarı ACL (erişim denetim listeleri) tarafından korunan olsa bile düz metin olarak kayıt defterinde parolalar gibi gizli depolamak için güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="48a59-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="48a59-106">Kayıt defteri ile çalışma sistem kaynaklarına uygun erişime izin vererek güvenliği tehlikeye atabilir veya bilgi korumalı.</span><span class="sxs-lookup"><span data-stu-id="48a59-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="48a59-107">Bu özellikleri kullanmak için olmalıdır okuma ve yazma izinlerinin <xref:System.Security.Permissions.RegistryPermissionAccess> kayıt defteri değişkenlerini erişimi denetleyen numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="48a59-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="48a59-108">Tam güven ile çalışan herhangi bir kod (varsayılan güvenlik ilkesi altında kullanıcının yerel sabit diskinde yüklü herhangi bir kod budur) kayıt defterine erişim için gerekli izinlere sahip.</span><span class="sxs-lookup"><span data-stu-id="48a59-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="48a59-109">Daha fazla bilgi için bkz: <xref:System.Security.Permissions.RegistryPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="48a59-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="48a59-110">Kayıt defteri değişkenlerini bellek konumlarda değil depolanmalıdır burada olmadan kod <xref:System.Security.Permissions.RegistryPermission> dosyalara erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48a59-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="48a59-111">Benzer şekilde, izinleri verme, işin tamamlanması için gereken en düşük ayrıcalıkları verin.</span><span class="sxs-lookup"><span data-stu-id="48a59-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="48a59-112">Kayıt defteri izni erişim değerleri tarafından tanımlanan <xref:System.Security.Permissions.RegistryPermissionAccess> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="48a59-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="48a59-113">Aşağıdaki tabloda üyeleri ayrıntılarını verir.</span><span class="sxs-lookup"><span data-stu-id="48a59-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="48a59-114">Değer</span><span class="sxs-lookup"><span data-stu-id="48a59-114">Value</span></span>|<span data-ttu-id="48a59-115">Kayıt defteri değişkenlerini erişimi</span><span class="sxs-lookup"><span data-stu-id="48a59-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="48a59-116">Oluşturma, okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="48a59-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="48a59-117">Create</span><span class="sxs-lookup"><span data-stu-id="48a59-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="48a59-118">Erişim yok</span><span class="sxs-lookup"><span data-stu-id="48a59-118">No access</span></span>|  
|`Read`|<span data-ttu-id="48a59-119">Oku</span><span class="sxs-lookup"><span data-stu-id="48a59-119">Read</span></span>|  
|`Write`|<span data-ttu-id="48a59-120">Write</span><span class="sxs-lookup"><span data-stu-id="48a59-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="48a59-121">Kayıt defteri anahtarlarını değerlerde denetleniyor</span><span class="sxs-lookup"><span data-stu-id="48a59-121">Checking Values in Registry Keys</span></span>  
 <span data-ttu-id="48a59-122">Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="48a59-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="48a59-123">Başka bir işlem, belki de kötü amaçlı bir değer önceden oluşturduğunuz ve buna erişiminiz.</span><span class="sxs-lookup"><span data-stu-id="48a59-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="48a59-124">Kayıt defteri değerindeki veri geçirdiğinizde, verileri başka bir işlem mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="48a59-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="48a59-125">Bunu önlemek için kullanmak `GetValue` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48a59-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="48a59-126">Döndürdüğü `Nothing` anahtarı zaten mevcut değilse.</span><span class="sxs-lookup"><span data-stu-id="48a59-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="48a59-127">Kayıt defteri bir Web uygulamasından okurken, geçerli kullanıcının kimliğini kimlik doğrulaması ve kimliğe bürünme Web uygulamasında uygulanan bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="48a59-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a59-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48a59-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [<span data-ttu-id="48a59-129">Okuma ve kayıt defterine yazma</span><span class="sxs-lookup"><span data-stu-id="48a59-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
