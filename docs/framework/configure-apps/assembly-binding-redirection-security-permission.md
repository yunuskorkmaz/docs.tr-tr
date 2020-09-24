---
title: Derleme Bağlama Yönlendirmesi Güvenlik İzni
description: .NET 'teki bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için gereken güvenlik izni hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: 2de2c50f5adb9e9fa36ea015ef498e9953c83005
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165227"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="5b2b3-103">Derleme Bağlama Yönlendirmesi Güvenlik İzni</span><span class="sxs-lookup"><span data-stu-id="5b2b3-103">Assembly Binding Redirection Security Permission</span></span>

<span data-ttu-id="5b2b3-104">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-104">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="5b2b3-105">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-105">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="5b2b3-106"><xref:System.Security.Permissions.SecurityPermissionFlag>' De bayrak ayarlanarak izin verilir <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="5b2b3-106">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="5b2b3-107">Yönetilen derlemelerin varsayılan olarak izinleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-107">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="5b2b3-108">Güvenlik izni, Güvenilen bölge (yerel makine) ve Intranet bölgesinde çalışan uygulamalara verilir.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-108">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="5b2b3-109">Internet bölgesinde çalışan uygulamaların, derleme bağlama yeniden yönlendirmesi gerçekleştirmekten kesinlikle izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-109">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="5b2b3-110">Derleme yeniden yönlendirmesi, bileşen yayımcısı tarafından denetlenen bir yayımcı ilke dosyasında ya da yönetici tarafından denetlenen makine yapılandırma dosyasında gerçekleştirilirse, izin gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-110">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="5b2b3-111">Ancak, bir uygulamanın [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) uygulama yapılandırma dosyasındaki öğesini kullanarak yayımcı ilkesini açıkça yoksayması için izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-111">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="5b2b3-112">Aşağıdaki tabloda, **Bindingyönlendirmeler** bayrağıyla ilgili varsayılan güvenlik ayarları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-112">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="5b2b3-113">Bölge</span><span class="sxs-lookup"><span data-stu-id="5b2b3-113">Zone</span></span>|<span data-ttu-id="5b2b3-114">Bindingyönlendirmeler bayrak ayarı</span><span class="sxs-lookup"><span data-stu-id="5b2b3-114">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="5b2b3-115">Güvenilen bölge (yerel makine)</span><span class="sxs-lookup"><span data-stu-id="5b2b3-115">Trusted Zone (local machine)</span></span>|<span data-ttu-id="5b2b3-116">**DAYANıR**</span><span class="sxs-lookup"><span data-stu-id="5b2b3-116">**ON**</span></span>|  
|<span data-ttu-id="5b2b3-117">Intranet bölgesi</span><span class="sxs-lookup"><span data-stu-id="5b2b3-117">Intranet Zone</span></span>|<span data-ttu-id="5b2b3-118">**DAYANıR**</span><span class="sxs-lookup"><span data-stu-id="5b2b3-118">**ON**</span></span>|  
|<span data-ttu-id="5b2b3-119">Internet Bölgesi</span><span class="sxs-lookup"><span data-stu-id="5b2b3-119">Internet Zone</span></span>|<span data-ttu-id="5b2b3-120">**DıŞıNA**</span><span class="sxs-lookup"><span data-stu-id="5b2b3-120">**OFF**</span></span>|  
|<span data-ttu-id="5b2b3-121">Güvenilmeyen bölgeler</span><span class="sxs-lookup"><span data-stu-id="5b2b3-121">Untrusted zones</span></span>|<span data-ttu-id="5b2b3-122">**DıŞıNA**</span><span class="sxs-lookup"><span data-stu-id="5b2b3-122">**OFF**</span></span>|  
  
 <span data-ttu-id="5b2b3-123">Bir yönetici, belirli bir bilgisayardaki belirli senaryoları desteklemek veya kısıtlamak için bu güvenlik ayarlarını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-123">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="5b2b3-124">Varsayılan değer olan **Bindingyönlendirmeler** bayrak ayarını değiştirmek için araç yoktur; bir yönetici, kullanıcının bilgisayarındaki Security.config dosyasını el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-124">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2b3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b2b3-125">See also</span></span>

- <span data-ttu-id="5b2b3-126">[Yayımcı Ilke dosyaları ve yan yana yürütme](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5b2b3-126">[Publisher Policy Files and Side-by-Side Execution](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="5b2b3-127">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="5b2b3-127">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="5b2b3-128">Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="5b2b3-128">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
