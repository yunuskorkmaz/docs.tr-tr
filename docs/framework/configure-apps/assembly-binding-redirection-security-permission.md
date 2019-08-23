---
title: Derleme Bağlama Yönlendirmesi Güvenlik İzni
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921382"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="c862c-102">Derleme Bağlama Yönlendirmesi Güvenlik İzni</span><span class="sxs-lookup"><span data-stu-id="c862c-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="c862c-103">Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir.</span><span class="sxs-lookup"><span data-stu-id="c862c-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="c862c-104">Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c862c-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="c862c-105">' De <xref:System.Security.Permissions.SecurityPermissionFlag> bayrak ayarlanarak izin verilir. <xref:System.Security.Permissions.SecurityPermission></span><span class="sxs-lookup"><span data-stu-id="c862c-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="c862c-106">Yönetilen derlemelerin varsayılan olarak izinleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="c862c-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="c862c-107">Güvenlik izni, Güvenilen bölge (yerel makine) ve Intranet bölgesinde çalışan uygulamalara verilir.</span><span class="sxs-lookup"><span data-stu-id="c862c-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="c862c-108">Internet bölgesinde çalışan uygulamaların, derleme bağlama yeniden yönlendirmesi gerçekleştirmekten kesinlikle izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="c862c-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="c862c-109">Derleme yeniden yönlendirmesi, bileşen yayımcısı tarafından denetlenen bir yayımcı ilke dosyasında ya da yönetici tarafından denetlenen makine yapılandırma dosyasında gerçekleştirilirse, izin gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c862c-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="c862c-110">Ancak, bir uygulamanın uygulama yapılandırma dosyasında [ \<publisherPolicy apply = "No"/>](./file-schema/runtime/publisherpolicy-element.md) öğesini kullanarak yayımcı ilkesini açıkça yoksayması için izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="c862c-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="c862c-111">Aşağıdaki tabloda, **Bindingyönlendirmeler** bayrağıyla ilgili varsayılan güvenlik ayarları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c862c-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="c862c-112">Bölge</span><span class="sxs-lookup"><span data-stu-id="c862c-112">Zone</span></span>|<span data-ttu-id="c862c-113">Bindingyönlendirmeler bayrak ayarı</span><span class="sxs-lookup"><span data-stu-id="c862c-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="c862c-114">Güvenilen bölge (yerel makine)</span><span class="sxs-lookup"><span data-stu-id="c862c-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="c862c-115">**DAYANIR**</span><span class="sxs-lookup"><span data-stu-id="c862c-115">**ON**</span></span>|  
|<span data-ttu-id="c862c-116">Intranet bölgesi</span><span class="sxs-lookup"><span data-stu-id="c862c-116">Intranet Zone</span></span>|<span data-ttu-id="c862c-117">**DAYANIR**</span><span class="sxs-lookup"><span data-stu-id="c862c-117">**ON**</span></span>|  
|<span data-ttu-id="c862c-118">Internet Bölgesi</span><span class="sxs-lookup"><span data-stu-id="c862c-118">Internet Zone</span></span>|<span data-ttu-id="c862c-119">**DIŞINA**</span><span class="sxs-lookup"><span data-stu-id="c862c-119">**OFF**</span></span>|  
|<span data-ttu-id="c862c-120">Güvenilmeyen bölgeler</span><span class="sxs-lookup"><span data-stu-id="c862c-120">Untrusted zones</span></span>|<span data-ttu-id="c862c-121">**DIŞINA**</span><span class="sxs-lookup"><span data-stu-id="c862c-121">**OFF**</span></span>|  
  
 <span data-ttu-id="c862c-122">Bir yönetici, belirli bir bilgisayardaki belirli senaryoları desteklemek veya kısıtlamak için bu güvenlik ayarlarını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c862c-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="c862c-123">Varsayılan değer olan **Bindingyönlendirmeler** bayrak ayarını değiştirmek için araç yoktur; bir yönetici, kullanıcının bilgisayarındaki Security. config dosyasını el ile düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c862c-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c862c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c862c-124">See also</span></span>

- <span data-ttu-id="c862c-125">[Yayımcı Ilke dosyaları ve yan yana yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c862c-125">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="c862c-126">Nasıl yapılır: Otomatik bağlama yeniden yönlendirmeyi etkinleştirme ve devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="c862c-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="c862c-127">Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="c862c-127">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
