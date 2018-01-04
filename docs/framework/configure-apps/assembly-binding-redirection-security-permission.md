---
title: "Derleme Bağlama Yönlendirmesi Güvenlik İzni"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1bd25dd0444c428e000371abe494e62b258eaa63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="b5c7d-102">Derleme Bağlama Yönlendirmesi Güvenlik İzni</span><span class="sxs-lookup"><span data-stu-id="b5c7d-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="b5c7d-103">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="b5c7d-104">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="b5c7d-105">Ayarlayarak iznine sahip <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="b5c7d-106">Yönetilen derlemeler varsayılan olarak bir izniniz yok.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="b5c7d-107">Intranet bölgesi ve Güvenilen Bölge (yerel makine) içinde çalışan uygulamalar için güvenlik izni verilir.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="b5c7d-108">Internet bölgesinde çalışan uygulamalar Derleme bağlaması yeniden yönlendirme gerçekleştiren kesinlikle yasaktır.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="b5c7d-109">Derleme yeniden yönlendirme bileşen yayımcı tarafından denetlenen bir yayımcı ilkesi dosyası ya da yönetici tarafından denetlenen makine yapılandırma dosyası gerçekleştirdiyseniz izni gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="b5c7d-110">Ancak, bir uygulama ilkesi publisher'ı kullanarak açıkça yoksaymak izni gereklidir [ \<publisherPolicy uygulamak = "Hayır" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="b5c7d-111">Varsayılan güvenlik ayarlarını aşağıdaki tabloda gösterilmektedir **BindingRedirects** bayrağı.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="b5c7d-112">Bölge</span><span class="sxs-lookup"><span data-stu-id="b5c7d-112">Zone</span></span>|<span data-ttu-id="b5c7d-113">BindingRedirects bayrağı ayarlama</span><span class="sxs-lookup"><span data-stu-id="b5c7d-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="b5c7d-114">Güvenilir bölgeye (yerel makine)</span><span class="sxs-lookup"><span data-stu-id="b5c7d-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="b5c7d-115">**AÇIK**</span><span class="sxs-lookup"><span data-stu-id="b5c7d-115">**ON**</span></span>|  
|<span data-ttu-id="b5c7d-116">İntranet bölgesi</span><span class="sxs-lookup"><span data-stu-id="b5c7d-116">Intranet Zone</span></span>|<span data-ttu-id="b5c7d-117">**AÇIK**</span><span class="sxs-lookup"><span data-stu-id="b5c7d-117">**ON**</span></span>|  
|<span data-ttu-id="b5c7d-118">Internet Bölgesi</span><span class="sxs-lookup"><span data-stu-id="b5c7d-118">Internet Zone</span></span>|<span data-ttu-id="b5c7d-119">**KAPALI**</span><span class="sxs-lookup"><span data-stu-id="b5c7d-119">**OFF**</span></span>|  
|<span data-ttu-id="b5c7d-120">Güvenilmeyen bölgeleri</span><span class="sxs-lookup"><span data-stu-id="b5c7d-120">Untrusted zones</span></span>|<span data-ttu-id="b5c7d-121">**KAPALI**</span><span class="sxs-lookup"><span data-stu-id="b5c7d-121">**OFF**</span></span>|  
  
 <span data-ttu-id="b5c7d-122">Bir yönetici veya kısıtlama verilen bir bilgisayardaki belirli senaryoları desteklemek üzere bu güvenlik ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="b5c7d-123">Değiştirmek için hiçbir araç vardır **BindingRedirects** varsayılandan; ayarlama bayrağı yönetici el ile bir kullanıcının bilgisayarda Security.config dosyasını düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c7d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5c7d-124">See Also</span></span>  
 [<span data-ttu-id="b5c7d-125">Yayımcı ilke dosyaları ve yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="b5c7d-125">Publisher Policy Files and Side-by-Side Execution</span></span>](http://msdn.microsoft.com/en-us/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="b5c7d-126">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="b5c7d-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="b5c7d-127">Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="b5c7d-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
