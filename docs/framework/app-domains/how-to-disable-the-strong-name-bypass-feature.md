---
title: 'Nasıl yapılır: Tanımlayıcı adlı atlama özelliğini devre dışı bırakma'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd4e5ea1907ec3de4536d09b3d76ca4956c8756d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494308"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="1f6a9-102">Nasıl yapılır: Tanımlayıcı adlı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="1f6a9-102">How to: Disable the Strong-Name Bypass Feature</span></span>
<span data-ttu-id="1f6a9-103">İle .NET Framework sürüm 3.5 Service Pack 1 (SP1) başlayarak, tam güvene bir derleme yüklendiğinde tanımlayıcı ad imzaları doğrulanmaz <xref:System.AppDomain> gibi varsayılan nesne <xref:System.AppDomain> için `MyComputer` bölge.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="1f6a9-104">Bu atlama özelliğini tanımlayıcı ad adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="1f6a9-105">İçin tam güven ortamında, talepleri <xref:System.Security.Permissions.StrongNameIdentityPermission> imzalı için tam güven derlemeleri imzalarına bağımsız olarak her zaman başarılı.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="1f6a9-106">Tek kısıtlama, kendi bölgesine tam güvenilir olduğundan derleme tam güvenilir olması gerekliliğidir.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="1f6a9-107">Tanımlayıcı adı bir faktör Bu koşullar altında olmadığı için bunu doğrulanması için bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="1f6a9-108">Tanımlayıcı ad imzası doğrulama atlama önemli performans geliştirmeleri sunar.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="1f6a9-109">Bu gecikme-imzalı değil ve bir tam güvene yüklenen herhangi bir tam güven derleme atlama özelliğini uygular <xref:System.AppDomain> tarafından belirtilen dizinden kendi <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="1f6a9-110">Bir kayıt defteri anahtarı değerini ayarlayarak bir bilgisayarda tüm uygulamalar için atlama özelliğini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="1f6a9-111">Uygulama yapılandırma dosyası kullanarak tek bir uygulama ayarı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="1f6a9-112">Kayıt defteri anahtarı tarafından devre dışı bırakılırsa atlama özelliği tek bir uygulama için yeniden devreye sokmanız olamaz.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="1f6a9-113">Atlama özelliğini geçersiz kıldığınızda, tanımlayıcı ad doğruluğu yalnızca doğrulanır. için işaretli bir <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="1f6a9-114">Belirli bir tanımlayıcı ad doğrulamak istiyorsanız bu onay ayrı olarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1f6a9-115">Tanımlayıcı ad doğrulama zorlama olanağı, aşağıdaki yordamda açıklandığı gibi bir kayıt defteri anahtarı bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="1f6a9-116">Bir uygulama bu kayıt defteri anahtarına erişim için erişim denetim listesi (ACL) iznine sahip olmayan bir hesap altında çalışıyorsa, verimsiz bir ayardır.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="1f6a9-117">Böylece tüm derlemeler için okunabilir ACL hakları bu anahtar için yapılandırıldığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="1f6a9-118">Tanımlayıcı ad atlama özelliği tüm uygulamalar için devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="1f6a9-118">To disable the strong-name bypass feature for all applications</span></span>  
  
-   <span data-ttu-id="1f6a9-119">32-bit bilgisayarlarda, sistem kayıt defterinde DWORD girişini adlı 0 değeri ile oluşturma `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında\\. NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
-   <span data-ttu-id="1f6a9-120">64-bit bilgisayarlarda, sistem kayıt defterinde DWORD girişini adlı 0 değeri ile oluşturma `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında\\. NETFramework ve HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework anahtarları.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="1f6a9-121">Tanımlayıcı ad atlama özelliği tek bir uygulama için devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="1f6a9-121">To disable the strong-name bypass feature for a single application</span></span>  
  
1.  <span data-ttu-id="1f6a9-122">Uygulama yapılandırma dosyasını oluşturun veya açın.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="1f6a9-123">Uygulama yapılandırma dosyaları bölümünde bu dosya hakkında daha fazla bilgi için bkz. [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f6a9-123">For more information about this file, see the Application Configuration Files section in [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
2.  <span data-ttu-id="1f6a9-124">Şu girişi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1f6a9-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="1f6a9-125">Yapılandırma dosyası ayarı kaldırarak veya öznitelik "true" ayarını, uygulama için atlama özelliğini geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to "true".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f6a9-126">Yalnızca bilgisayar için atlama özelliği etkinse, bir uygulama için tanımlayıcı ad doğrulama açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="1f6a9-127">Atlama özelliği, bilgisayarı kapatılmış, tüm uygulamalar için güçlü adlar doğrulanır ve tek bir uygulama için doğrulamayı atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6a9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f6a9-128">See also</span></span>
- [<span data-ttu-id="1f6a9-129">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="1f6a9-129">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="1f6a9-130">\<bypassTrustedAppStrongNames > öğesi</span><span class="sxs-lookup"><span data-stu-id="1f6a9-130">\<bypassTrustedAppStrongNames> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="1f6a9-131">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="1f6a9-131">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
