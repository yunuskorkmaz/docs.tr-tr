---
title: Derleme Bağlama Yönlendirmesi Güvenlik İzni
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921382"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="a221d-102">Derleme Bağlama Yönlendirmesi Güvenlik İzni</span><span class="sxs-lookup"><span data-stu-id="a221d-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="a221d-103">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="a221d-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="a221d-104">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a221d-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="a221d-105"><xref:System.Security.Permissions.SecurityPermissionFlag>' De bayrak ayarlanarak izin verilir <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="a221d-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="a221d-106">Yönetilen derlemelerin varsayılan olarak izinleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="a221d-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="a221d-107">Güvenlik izni, Güvenilen bölge (yerel makine) ve Intranet bölgesinde çalışan uygulamalara verilir.</span><span class="sxs-lookup"><span data-stu-id="a221d-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="a221d-108">Internet bölgesinde çalışan uygulamaların, derleme bağlama yeniden yönlendirmesi gerçekleştirmekten kesinlikle izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="a221d-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="a221d-109">Derleme yeniden yönlendirmesi, bileşen yayımcısı tarafından denetlenen bir yayımcı ilke dosyasında ya da yönetici tarafından denetlenen makine yapılandırma dosyasında gerçekleştirilirse, izin gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a221d-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="a221d-110">Ancak, bir uygulamanın [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) uygulama yapılandırma dosyasındaki öğesini kullanarak yayımcı ilkesini açıkça yoksayması için izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="a221d-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="a221d-111">Aşağıdaki tabloda, **Bindingyönlendirmeler** bayrağıyla ilgili varsayılan güvenlik ayarları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a221d-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="a221d-112">Bölge</span><span class="sxs-lookup"><span data-stu-id="a221d-112">Zone</span></span>|<span data-ttu-id="a221d-113">Bindingyönlendirmeler bayrak ayarı</span><span class="sxs-lookup"><span data-stu-id="a221d-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="a221d-114">Güvenilen bölge (yerel makine)</span><span class="sxs-lookup"><span data-stu-id="a221d-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="a221d-115">**DAYANıR**</span><span class="sxs-lookup"><span data-stu-id="a221d-115">**ON**</span></span>|  
|<span data-ttu-id="a221d-116">Intranet bölgesi</span><span class="sxs-lookup"><span data-stu-id="a221d-116">Intranet Zone</span></span>|<span data-ttu-id="a221d-117">**DAYANıR**</span><span class="sxs-lookup"><span data-stu-id="a221d-117">**ON**</span></span>|  
|<span data-ttu-id="a221d-118">Internet Bölgesi</span><span class="sxs-lookup"><span data-stu-id="a221d-118">Internet Zone</span></span>|<span data-ttu-id="a221d-119">**DıŞıNA**</span><span class="sxs-lookup"><span data-stu-id="a221d-119">**OFF**</span></span>|  
|<span data-ttu-id="a221d-120">Güvenilmeyen bölgeler</span><span class="sxs-lookup"><span data-stu-id="a221d-120">Untrusted zones</span></span>|<span data-ttu-id="a221d-121">**DıŞıNA**</span><span class="sxs-lookup"><span data-stu-id="a221d-121">**OFF**</span></span>|  
  
 <span data-ttu-id="a221d-122">Bir yönetici, belirli bir bilgisayardaki belirli senaryoları desteklemek veya kısıtlamak için bu güvenlik ayarlarını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a221d-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="a221d-123">Varsayılan değer olan **Bindingyönlendirmeler** bayrak ayarını değiştirmek için araç yoktur; bir yönetici, kullanıcının bilgisayarındaki Security. config dosyasını el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a221d-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a221d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a221d-124">See also</span></span>

- <span data-ttu-id="a221d-125">[Yayımcı Ilke dosyaları ve yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a221d-125">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="a221d-126">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="a221d-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="a221d-127">Yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="a221d-127">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
