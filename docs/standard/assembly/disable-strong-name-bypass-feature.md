---
title: 'Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma'
description: Güçlü ad atlama, .NET 'teki tam güvenilir etki alanlarında imza doğrulamasını atlar. Tek bir uygulama veya tüm uygulamalar için bu özelliği geçersiz kılabilirsiniz.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: 1914997b322591d8deda13d00192bc5f60d81ca2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378491"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="c53a8-104">Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="c53a8-104">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="c53a8-105">.NET Framework sürüm 3,5 hizmet paketi 1 ' den (SP1) başlayarak, bir derleme bir tam güven nesnesine yüklendiğinde (örneğin, <xref:System.AppDomain> bölge için varsayılan) tanımlayıcı ad imzaları doğrulanmaz <xref:System.AppDomain> `MyComputer` .</span><span class="sxs-lookup"><span data-stu-id="c53a8-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="c53a8-106">Bu, tanımlayıcı ad atlama özelliği olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c53a8-106">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="c53a8-107">Tam güven ortamında, <xref:System.Security.Permissions.StrongNameIdentityPermission> imzalarından bağımsız olarak imzalı, tam güvenle derlemeler için her zaman başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="c53a8-107">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="c53a8-108">Tek kısıtlama, kendi bölgesi tam güvenilir olduğu için derlemenin tam güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c53a8-108">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="c53a8-109">Tanımlayıcı ad bu koşullar altında bir belirleme faktörü olmadığından, bunun doğrulanması için bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="c53a8-109">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="c53a8-110">Tanımlayıcı ad imzalarının doğrulanmasını atlamak, önemli performans iyileştirmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c53a8-110">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="c53a8-111">Atlama özelliği, gecikmeli imzalanmış olmayan ve <xref:System.AppDomain> özelliği tarafından belirtilen dizinden herhangi bir tam güvenle yüklenmiş tüm tam güven derlemeleri için geçerlidir <xref:System.AppDomainSetup.ApplicationBase%2A> .</span><span class="sxs-lookup"><span data-stu-id="c53a8-111">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="c53a8-112">Bir kayıt defteri anahtarı değeri ayarlayarak, bir bilgisayardaki tüm uygulamalar için atlama özelliğini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c53a8-112">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="c53a8-113">Bir uygulama yapılandırma dosyası kullanarak tek bir uygulama için ayarı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c53a8-113">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="c53a8-114">Kayıt defteri anahtarı tarafından devre dışı bırakılmışsa, tek bir uygulama için atlama özelliğini eski durumuna getiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c53a8-114">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="c53a8-115">Atlama özelliğini geçersiz kıldığınızda, tanımlayıcı ad yalnızca doğruluk için onaylanır; bir için onay değildir <xref:System.Security.Permissions.StrongNameIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="c53a8-115">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="c53a8-116">Belirli bir tanımlayıcı adı doğrulamak istiyorsanız, bu denetimi ayrı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c53a8-116">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c53a8-117">Güçlü ad doğrulamasını zorlama özelliği, aşağıdaki yordamda açıklandığı gibi bir kayıt defteri anahtarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c53a8-117">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="c53a8-118">Bir uygulama, bu kayıt defteri anahtarına erişim denetim listesi (ACL) iznine sahip olmayan bir hesap altında çalışıyorsa, ayar etkisiz olur.</span><span class="sxs-lookup"><span data-stu-id="c53a8-118">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="c53a8-119">Tüm derlemeler için okunabilmesi için ACL haklarının bu anahtar için yapılandırıldığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c53a8-119">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="c53a8-120">Tüm uygulamalar için tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="c53a8-120">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="c53a8-121">32 bit bilgisayarlarda, sistem kayıt defterinde, `AllowStrongNameBypass` HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft altında adı 0 olan BIR DWORD girişi oluşturun \\ . NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c53a8-121">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="c53a8-122">64 bit bilgisayarlarda, sistem kayıt defterinde, `AllowStrongNameBypass` HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft altında adı 0 olan BIR DWORD girişi oluşturun \\ . NETFramework ve HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework anahtarları.</span><span class="sxs-lookup"><span data-stu-id="c53a8-122">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="c53a8-123">Tek bir uygulama için tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="c53a8-123">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="c53a8-124">Uygulama yapılandırma dosyasını açın veya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c53a8-124">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="c53a8-125">Bu dosya hakkında daha fazla bilgi için [uygulamaları yapılandırma](../../framework/configure-apps/index.md)konusunun uygulama yapılandırma dosyaları bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c53a8-125">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="c53a8-126">Aşağıdaki girişi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c53a8-126">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="c53a8-127">Yapılandırma dosyası ayarını kaldırarak veya özniteliğini olarak ayarlayarak, uygulamanın atlama özelliğini geri yükleyebilirsiniz `true` .</span><span class="sxs-lookup"><span data-stu-id="c53a8-127">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c53a8-128">Yalnızca bilgisayar için atlama özelliği etkinse, bir uygulama için tanımlayıcı ad doğrulamayı açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c53a8-128">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="c53a8-129">Bilgisayar için atlama özelliği kapatılmışsa, tüm uygulamalar için tanımlayıcı adlar onaylanır ve tek bir uygulama için doğrulamayı atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c53a8-129">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c53a8-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c53a8-130">See also</span></span>

- [<span data-ttu-id="c53a8-131">Sn. exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="c53a8-131">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="c53a8-132">\<bypassTrustedAppStrongNames> öğesi</span><span class="sxs-lookup"><span data-stu-id="c53a8-132">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="c53a8-133">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="c53a8-133">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
