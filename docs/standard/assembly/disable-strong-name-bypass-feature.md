---
title: 'Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141110"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="ef692-102">Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="ef692-102">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="ef692-103">.NET Framework sürüm 3,5 hizmet paketi 1 ' den (SP1) başlayarak, bir derleme bir tam güvenle <xref:System.AppDomain> nesnesine yüklendiğinde, `MyComputer` bölgesi için varsayılan <xref:System.AppDomain> gibi tanımlayıcı ad imzaları doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="ef692-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="ef692-104">Bu, tanımlayıcı ad atlama özelliği olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef692-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="ef692-105">Tam güven ortamında, imzaları ne olursa olsun imzalı, tam güvenle derlemeler için <xref:System.Security.Permissions.StrongNameIdentityPermission> talepleri her zaman başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="ef692-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="ef692-106">Tek kısıtlama, kendi bölgesi tam güvenilir olduğu için derlemenin tam güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef692-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="ef692-107">Tanımlayıcı ad bu koşullar altında bir belirleme faktörü olmadığından, bunun doğrulanması için bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="ef692-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="ef692-108">Tanımlayıcı ad imzalarının doğrulanmasını atlamak, önemli performans iyileştirmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef692-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="ef692-109">Atlama özelliği, Gecikmeli imzalı olmayan ve <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği tarafından belirtilen dizinden herhangi bir tam güvenle <xref:System.AppDomain> yüklenen tüm tam güven derlemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ef692-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="ef692-110">Bir kayıt defteri anahtarı değeri ayarlayarak, bir bilgisayardaki tüm uygulamalar için atlama özelliğini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef692-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="ef692-111">Bir uygulama yapılandırma dosyası kullanarak tek bir uygulama için ayarı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef692-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="ef692-112">Kayıt defteri anahtarı tarafından devre dışı bırakılmışsa, tek bir uygulama için atlama özelliğini eski durumuna getiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef692-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="ef692-113">Atlama özelliğini geçersiz kıldığınızda, tanımlayıcı ad yalnızca doğruluk için onaylanır; <xref:System.Security.Permissions.StrongNameIdentityPermission>için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="ef692-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="ef692-114">Belirli bir tanımlayıcı adı doğrulamak istiyorsanız, bu denetimi ayrı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef692-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef692-115">Güçlü ad doğrulamasını zorlama özelliği, aşağıdaki yordamda açıklandığı gibi bir kayıt defteri anahtarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ef692-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="ef692-116">Bir uygulama, bu kayıt defteri anahtarına erişim denetim listesi (ACL) iznine sahip olmayan bir hesap altında çalışıyorsa, ayar etkisiz olur.</span><span class="sxs-lookup"><span data-stu-id="ef692-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="ef692-117">Tüm derlemeler için okunabilmesi için ACL haklarının bu anahtar için yapılandırıldığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef692-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="ef692-118">Tüm uygulamalar için tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="ef692-118">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="ef692-119">32 bit bilgisayarlarda, sistem kayıt defterinde, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\altında `AllowStrongNameBypass` adlı değeri 0 olan bir DWORD girişi oluşturun. NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="ef692-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="ef692-120">64 bit bilgisayarlarda, sistem kayıt defterinde, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\altında `AllowStrongNameBypass` adlı değeri 0 olan bir DWORD girişi oluşturun. NETFramework ve HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework anahtarları.</span><span class="sxs-lookup"><span data-stu-id="ef692-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="ef692-121">Tek bir uygulama için tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="ef692-121">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="ef692-122">Uygulama yapılandırma dosyasını açın veya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef692-122">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="ef692-123">Bu dosya hakkında daha fazla bilgi için [uygulamaları yapılandırma](../../framework/configure-apps/index.md)konusunun uygulama yapılandırma dosyaları bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ef692-123">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="ef692-124">Aşağıdaki girişi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ef692-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="ef692-125">Yapılandırma dosyası ayarını kaldırarak veya özniteliğini `true`olarak ayarlayarak, uygulamanın atlama özelliğini geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef692-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef692-126">Yalnızca bilgisayar için atlama özelliği etkinse, bir uygulama için tanımlayıcı ad doğrulamayı açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef692-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="ef692-127">Bilgisayar için atlama özelliği kapatılmışsa, tüm uygulamalar için tanımlayıcı adlar onaylanır ve tek bir uygulama için doğrulamayı atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ef692-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef692-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef692-128">See also</span></span>

- [<span data-ttu-id="ef692-129">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="ef692-129">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="ef692-130">\<bypassTrustedAppStrongNames > öğesi</span><span class="sxs-lookup"><span data-stu-id="ef692-130">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="ef692-131">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="ef692-131">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
