---
title: Derleme Bağlama Yönlendirmesi Güvenlik İzni
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b9b9ac5c4e8ce08b9f926b0cdf7149dbdd9ac2da
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501439"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="3899f-102">Derleme Bağlama Yönlendirmesi Güvenlik İzni</span><span class="sxs-lookup"><span data-stu-id="3899f-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="3899f-103">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="3899f-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="3899f-104">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3899f-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="3899f-105">İzin ayarlanarak verilir <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="3899f-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="3899f-106">Yönetilen derlemeler varsayılan olarak izniniz yok.</span><span class="sxs-lookup"><span data-stu-id="3899f-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="3899f-107">Güvenilen Bölge (yerel makine) ve Intranet bölgesinde çalışan uygulamalar için güvenlik izni verilir.</span><span class="sxs-lookup"><span data-stu-id="3899f-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="3899f-108">Internet bölgesinde çalışan uygulamalar, kesinlikle derleme bağlama yeniden yönlendirmesi gerçekleştirmesini yüklenmeleri yasaktır.</span><span class="sxs-lookup"><span data-stu-id="3899f-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="3899f-109">Derleme yeniden yönlendirme bileşenin yayımcı tarafından denetlenen bir yayımcı ilkesi dosyası ya da yönetici tarafından denetlenen makine yapılandırma dosyası gerçekleştirilirse izin gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3899f-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="3899f-110">Ancak, yayımcı ilkesi kullanarak açıkça yoksaymak bir uygulama için izin gerekiyor [ \<publisherPolicy uygulama = "Hayır" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="3899f-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="3899f-111">Aşağıdaki tabloda, varsayılan güvenlik ayarlarını gösterir. **SecurityPermission** bayrağı.</span><span class="sxs-lookup"><span data-stu-id="3899f-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="3899f-112">Bölge</span><span class="sxs-lookup"><span data-stu-id="3899f-112">Zone</span></span>|<span data-ttu-id="3899f-113">SecurityPermission bayrağını ayarlama</span><span class="sxs-lookup"><span data-stu-id="3899f-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="3899f-114">Güvenilir bölgeye (yerel makine)</span><span class="sxs-lookup"><span data-stu-id="3899f-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="3899f-115">**AÇIK**</span><span class="sxs-lookup"><span data-stu-id="3899f-115">**ON**</span></span>|  
|<span data-ttu-id="3899f-116">Intranet bölgesi</span><span class="sxs-lookup"><span data-stu-id="3899f-116">Intranet Zone</span></span>|<span data-ttu-id="3899f-117">**AÇIK**</span><span class="sxs-lookup"><span data-stu-id="3899f-117">**ON**</span></span>|  
|<span data-ttu-id="3899f-118">Internet Bölgesi</span><span class="sxs-lookup"><span data-stu-id="3899f-118">Internet Zone</span></span>|<span data-ttu-id="3899f-119">**KAPALI**</span><span class="sxs-lookup"><span data-stu-id="3899f-119">**OFF**</span></span>|  
|<span data-ttu-id="3899f-120">Güvenilmeyen bölgeleri</span><span class="sxs-lookup"><span data-stu-id="3899f-120">Untrusted zones</span></span>|<span data-ttu-id="3899f-121">**KAPALI**</span><span class="sxs-lookup"><span data-stu-id="3899f-121">**OFF**</span></span>|  
  
 <span data-ttu-id="3899f-122">Bir yönetici veya kısıtlama belirli bir bilgisayardaki belirli senaryoları desteklemek üzere bu güvenlik ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3899f-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="3899f-123">Değiştirmek için araçları yoktur **SecurityPermission** ; varsayılan ayarı bayrağı yönetici el ile bir kullanıcının bilgisayarında Security.config dosyayı düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3899f-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3899f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3899f-124">See Also</span></span>  
 [<span data-ttu-id="3899f-125">Yayımcı ilkesi dosyaları ve yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="3899f-125">Publisher Policy Files and Side-by-Side Execution</span></span>](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="3899f-126">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="3899f-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="3899f-127">Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="3899f-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
