---
title: 'Nasıl yapılır: Tanımlayıcı Adlı Atlama Özelliğini Devre Dışı Bırakma'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9604969ea073b07af0eca8d481f5459ee15d099
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742425"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="b0605-102">Nasıl yapılır: Tanımlayıcı Adlı Atlama Özelliğini Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="b0605-102">How to: Disable the Strong-Name Bypass Feature</span></span>
<span data-ttu-id="b0605-103">İle .NET Framework sürüm 3.5 Service Pack 1 (SP1) başlayarak, tam güvene bir derleme yüklendiğinde güçlü ad imzaları doğrulanmaz <xref:System.AppDomain> varsayılan gibi nesne <xref:System.AppDomain> için `MyComputer` bölgesi.</span><span class="sxs-lookup"><span data-stu-id="b0605-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="b0605-104">Bu özellik güçlü-adı olarak atlamak için adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b0605-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="b0605-105">İçin tam güven ortamında, talep <xref:System.Security.Permissions.StrongNameIdentityPermission> imzalı için tam güven derlemeleri imzalarına bakılmaksızın her zaman başarılı.</span><span class="sxs-lookup"><span data-stu-id="b0605-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="b0605-106">Ve bölgesi tam olarak güvenilir olmadığı için derleme tam olarak güvenilir olması gerektiğini yalnızca kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="b0605-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="b0605-107">Güçlü ad bu koşullarda belirleyici faktör olmadığından doğrulanması için için bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="b0605-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="b0605-108">Tanımlayıcı adlı imza doğrulaması atlayarak önemli ölçüde performans artışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0605-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="b0605-109">Gecikme-imzalı değil ve hiçbir tam güvene yüklenen tüm tam güven derlemesi atlama özelliğini uygulandığı <xref:System.AppDomain> tarafından belirtilen dizinden kendi <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b0605-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="b0605-110">Kayıt defteri anahtarı değerini ayarlayarak bir bilgisayardaki tüm uygulamalar için atlama özelliğini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0605-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="b0605-111">Uygulama yapılandırma dosyası kullanarak tek bir uygulama ayarı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0605-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="b0605-112">Kayıt defteri anahtarı tarafından devre dışı bırakılırsa atlama özelliği tek bir uygulama için yeniden devreye sokmanız olamaz.</span><span class="sxs-lookup"><span data-stu-id="b0605-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="b0605-113">Atlama özelliğini geçersiz kıldığınızda, güçlü ad yalnızca doğruluğu doğrulanır. için işaretli bir <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="b0605-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="b0605-114">Belirli bir güçlü ad doğrulamak istiyorsanız, o onay ayrı olarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0605-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0605-115">Tanımlayıcı ad doğrulaması zorlama olanağı, aşağıdaki yordamda açıklandığı gibi bir kayıt defteri anahtarı bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b0605-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="b0605-116">Bir uygulama bu kayıt defteri anahtarına erişmek için erişim denetim listesi (ACL) iznine sahip olmayan bir hesap altında çalışıyorsa verimsiz bir ayardır.</span><span class="sxs-lookup"><span data-stu-id="b0605-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="b0605-117">Böylece tüm derlemeler için okunabilir ACL hakları bu anahtar için yapılandırılmış olan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="b0605-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="b0605-118">Tanımlayıcı adlı atlama özelliği tüm uygulamalar için devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="b0605-118">To disable the strong-name bypass feature for all applications</span></span>  
  
-   <span data-ttu-id="b0605-119">32-bit bilgisayarlarda, sistem kayıt defteri DWORD girdisi adlı 0 değerine sahip oluşturun `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında\\. NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="b0605-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
-   <span data-ttu-id="b0605-120">64-bit bilgisayarlarda, sistem kayıt defteri DWORD girdisi adlı 0 değerine sahip oluşturun `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında\\. NETFramework ve HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework anahtarları.</span><span class="sxs-lookup"><span data-stu-id="b0605-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="b0605-121">Tanımlayıcı adlı atlama özelliği tek bir uygulama için devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="b0605-121">To disable the strong-name bypass feature for a single application</span></span>  
  
1.  <span data-ttu-id="b0605-122">Uygulama yapılandırma dosyası oluşturun veya açın.</span><span class="sxs-lookup"><span data-stu-id="b0605-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="b0605-123">Uygulama yapılandırma dosyaları bölümünde bu dosya hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="b0605-123">For more information about this file, see the Application Configuration Files section in [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
2.  <span data-ttu-id="b0605-124">Aşağıdaki girişi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b0605-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="b0605-125">Yapılandırma dosyası ayarı kaldırarak veya öznitelik "true" olarak ayarlayarak uygulamanın atlama özelliğini geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0605-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to "true".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0605-126">Atlama özelliği bilgisayar için yalnızca etkinse, bir uygulama için tanımlayıcı ad doğrulama açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0605-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="b0605-127">Atlama özelliğini bilgisayarı kapatılmış, tanımlayıcı adlar tüm uygulamalar için doğrulanır ve tek bir uygulama doğrulamasını atlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b0605-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0605-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0605-128">See Also</span></span>  
 [<span data-ttu-id="b0605-129">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="b0605-129">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="b0605-130">\<bypassTrustedAppStrongNames > öğesi</span><span class="sxs-lookup"><span data-stu-id="b0605-130">\<bypassTrustedAppStrongNames> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [<span data-ttu-id="b0605-131">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="b0605-131">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
