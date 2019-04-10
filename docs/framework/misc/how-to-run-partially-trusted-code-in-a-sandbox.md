---
title: 'Nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caa9afcb1ab2ca53bba849c39651ca4cba3a9c77
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316537"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="5d218-102">Nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5d218-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="5d218-103">Korumalı alana alma kodu için kod erişim izinleri sınırlar bir kısıtlı güvenlik ortamı çalışan uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="5d218-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="5d218-104">Tamamen güvenmediğiniz bir kaynaktan bir yönetilen kitaplık varsa, örneğin, bu tam olarak güvenilir olarak çalıştırmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="5d218-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="5d218-105">Bunun yerine, gerek bekliyorsanız bu izinlerini sınırlayan bir korumalı alan içinde kod yerleştirmeniz gerekir (örneğin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni).</span><span class="sxs-lookup"><span data-stu-id="5d218-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="5d218-106">Korumalı alana alma, dağıtma ve kısmen güvenilen ortamlarda çalışacak kodu test etmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d218-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="5d218-107">Bir <xref:System.AppDomain> yönetilen uygulamalar için bir korumalı alan sağlayan etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="5d218-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="5d218-108">Kısmen güvenilen kod çalıştırmak için kullanılan uygulama etki alanları, içinde çalışırken kullanılabilir korumalı kaynakları tanımlayan izinlere sahip <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5d218-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="5d218-109">İçinde çalışan kod <xref:System.AppDomain> ilişkili izinler tarafından bağlı <xref:System.AppDomain> ve yalnızca belirtilen kaynaklara erişmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5d218-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="5d218-110"><xref:System.AppDomain> De içeren bir <xref:System.Security.Policy.StrongName> tam güvenilir olarak yüklenmesi için derlemeleri tanımlamak için kullanılan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="5d218-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="5d218-111">Oluşturucusu, böylece bir <xref:System.AppDomain> belirli yardımcı derlemeler tam olarak güvenilen veren yeni bir korumalı etki alanı başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="5d218-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="5d218-112">Derlemeleri tam olarak yüklenmesi için başka bir güvenilir genel derleme önbelleğinde yerleştirileceği bir seçenektir; Ancak, bu bilgisayar üzerinde oluşturulan tüm uygulama etki alanları olarak tam olarak güvenilen derlemelerde yükler.</span><span class="sxs-lookup"><span data-stu-id="5d218-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="5d218-113">Güçlü listesini adları destekleyen bir başına-<xref:System.AppDomain> sağlayan daha kısıtlayıcı belirleme kararı.</span><span class="sxs-lookup"><span data-stu-id="5d218-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="5d218-114">Kullanabileceğiniz <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> korumalı alanında çalışan uygulamalar için izin belirtmek üzere yöntem aşırı yüklemesini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5d218-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="5d218-115">Bu aşırı yüklemesi, istediğiniz kod erişim güvenliği düzeyini tam olarak belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d218-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="5d218-116">İçine yüklenen derlemeler bir <xref:System.AppDomain> Bu aşırı yüklemesi kullanarak ya da sahip olabilirsiniz belirtilen izin kümesine yalnızca veya tam güvenilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d218-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="5d218-117">Derleme genel derleme önbelleğinde ise tam güven veya listelenen verilir `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) dizi parametresi.</span><span class="sxs-lookup"><span data-stu-id="5d218-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="5d218-118">Sadece tam güvenilir olduğu bilinen derleme eklenmesi `fullTrustAssemblies` listesi.</span><span class="sxs-lookup"><span data-stu-id="5d218-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="5d218-119">Aşağıdaki imza aşırı yüklemesi vardır:</span><span class="sxs-lookup"><span data-stu-id="5d218-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="5d218-120">Parametreler için <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> yöntemi aşırı yüklemesi adını belirtin <xref:System.AppDomain>, için olan kanıtları <xref:System.AppDomain>, <xref:System.AppDomainSetup> korumalı alan ve izin kümesini kullanmak için tanımlayıcı adlar için uygulama temel tanımlayan nesne tamamen güvenilir derlemelerinin.</span><span class="sxs-lookup"><span data-stu-id="5d218-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="5d218-121">Güvenlik nedeniyle, uygulama tabanı belirtilen `info` barındırma uygulaması için temel uygulama parametresi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d218-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="5d218-122">İçin `grantSet` parametresi belirtebileceğiniz açıkça oluşturulan bir izin kümesi ya da bir standart izin kümesi tarafından oluşturulan <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5d218-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="5d218-123">Çoğu aksine <xref:System.AppDomain> yükler, için olan kanıtları <xref:System.AppDomain> (tarafından sağlanan `securityInfo` parametresi) kısmen güvenilen derlemelerde kodların belirlemek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="5d218-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="5d218-124">Bunun yerine, bağımsız olarak tarafından belirtilen `grantSet` parametresi.</span><span class="sxs-lookup"><span data-stu-id="5d218-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="5d218-125">Ancak, kanıt yalıtılmış depolama kapsamı belirleme gibi diğer amaçlar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d218-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="5d218-126">Bir korumalı alan içinde bir uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5d218-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="5d218-127">İzin güvenilmeyen uygulamanın verilecek kümesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5d218-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="5d218-128">En düşük izin vermesi <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni.</span><span class="sxs-lookup"><span data-stu-id="5d218-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="5d218-129">Ayrıca, ek izinler düşündüğünüz güvenilmeyen kod için güvenli verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="5d218-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="5d218-130">Aşağıdaki kod ile yalnızca olarak yeni bir izin oluşturur <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni.</span><span class="sxs-lookup"><span data-stu-id="5d218-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="5d218-131">Alternatif olarak, Internet gibi mevcut bir adlandırılmış izin kümesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d218-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="5d218-132"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> Yöntemi döndürür ya da bir `Internet` izin kümesi veya `LocalIntranet` izin dilimine bağlı olarak bir kanıt kümesi.</span><span class="sxs-lookup"><span data-stu-id="5d218-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <xref:System.Security.SecurityManager.GetStandardSandbox%2A> <span data-ttu-id="5d218-133">Ayrıca bazı başvurular geçirilen kanıt nesneler kimlik izinlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d218-133">also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="5d218-134">Barındırma sınıfı içeren derlemeyi imzalamayı (adlı `Sandboxer` Bu örnekte), güvenilmeyen kod çağırır.</span><span class="sxs-lookup"><span data-stu-id="5d218-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="5d218-135">Ekleme <xref:System.Security.Policy.StrongName> için derlemeyi imzalamak için kullanılan <xref:System.Security.Policy.StrongName> dizisi `fullTrustAssemblies` parametresinin <xref:System.AppDomain.CreateDomain%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="5d218-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="5d218-136">Barındıran sınıf çalıştırmalısınız kısmi güven kodunun yürütülmesini etkinleştirmek veya kısmi güven uygulama hizmet sunmak için tam olarak güvenilen olarak.</span><span class="sxs-lookup"><span data-stu-id="5d218-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="5d218-137">Bu, nasıl olduğunu okuyun, <xref:System.Security.Policy.StrongName> derleme:</span><span class="sxs-lookup"><span data-stu-id="5d218-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="5d218-138">Mscorlib ve System.dll gibi .NET framework derlemeleri genel bütünleştirilmiş kod önbelleğinden tam güvenilir yüklü oldukları için tam güven listesine eklenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5d218-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="5d218-139">Başlatma <xref:System.AppDomainSetup> parametresinin <xref:System.AppDomain.CreateDomain%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5d218-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="5d218-140">Bu parametre ile yeni ayarların birçoğunu denetleyebilirsiniz <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5d218-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="5d218-141"><xref:System.AppDomainSetup.ApplicationBase%2A> Özelliği önemli bir ayardır ve farklı olmalıdır <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği <xref:System.AppDomain> barındırma uygulaması.</span><span class="sxs-lookup"><span data-stu-id="5d218-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="5d218-142">Varsa <xref:System.AppDomainSetup.ApplicationBase%2A> ayarların aynı olduğundan, kısmi güven uygulama tanımlar, böylece kötüye kullanan bir özel durum (tam olarak güvenilir) yüklemek için barındırma uygulaması elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d218-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="5d218-143">Neden bir catch (özel durum) önerilmez başka bir nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="5d218-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="5d218-144">Uygulama ayarı tabanı konaktan farklı uygulama tabanı koruma alanlı uygulama açıkları riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="5d218-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="5d218-145">Çağrı <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> belirtilen parametreleri kullanarak uygulama etki alanı oluşturmak için yöntem aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="5d218-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="5d218-146">Bu yöntem imzası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5d218-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="5d218-147">Ek bilgiler:</span><span class="sxs-lookup"><span data-stu-id="5d218-147">Additional information:</span></span>  
  
    -   <span data-ttu-id="5d218-148">Bu, yalnızca aşırı yüklemesini <xref:System.AppDomain.CreateDomain%2A> gereken yöntemini bir <xref:System.Security.PermissionSet> bir parametre ve bu nedenle sağlayan tek bir aşırı yükleme bir kısmi güven ortamında bir uygulama yüklemek gibi.</span><span class="sxs-lookup"><span data-stu-id="5d218-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    -   <span data-ttu-id="5d218-149">`evidence` Parametresi bir izin kümesi hesaplamak için kullanılan değil; kimlik doğrulaması için .NET Framework'ün diğer özellikler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d218-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="5d218-150">Ayarı <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği `info` için bu aşırı yükleme parametresi zorunludur.</span><span class="sxs-lookup"><span data-stu-id="5d218-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    -   <span data-ttu-id="5d218-151">`fullTrustAssemblies` Parametresinin `params` oluşturmak gerekli değildir, yani anahtar sözcüğü bir <xref:System.Security.Policy.StrongName> dizi.</span><span class="sxs-lookup"><span data-stu-id="5d218-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="5d218-152">0, 1 veya daha fazla tanımlayıcı adlar parametre olarak geçirmeyi izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5d218-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    -   <span data-ttu-id="5d218-153">Uygulama etki alanı oluşturmak için kod yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="5d218-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="5d218-154">Kod içinde korumalı alana alma yüklemeye <xref:System.AppDomain> oluşturduğunuz.</span><span class="sxs-lookup"><span data-stu-id="5d218-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="5d218-155">Bu iki şekilde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="5d218-155">This can be done in two ways:</span></span>  
  
    -   <span data-ttu-id="5d218-156">Çağrı <xref:System.AppDomain.ExecuteAssembly%2A> derleme için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5d218-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    -   <span data-ttu-id="5d218-157">Kullanım <xref:System.Activator.CreateInstanceFrom%2A> sınıfından türetilen bir sınıfın bir örneğini oluşturmak için gereken yöntemini <xref:System.MarshalByRefObject> yeni <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5d218-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="5d218-158">Yeni parametreleri geçirmek kolaylaştırır ikinci yöntem tercih, çünkü <xref:System.AppDomain> örneği.</span><span class="sxs-lookup"><span data-stu-id="5d218-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="5d218-159"><xref:System.Activator.CreateInstanceFrom%2A> Yöntemi iki önemli özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="5d218-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    -   <span data-ttu-id="5d218-160">Derlemenizi içermeyen bir konumu gösteren bir kod tabanına kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d218-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    -   <span data-ttu-id="5d218-161">Oluşturma aşamasında yapabileceğiniz bir <xref:System.Security.CodeAccessPermission.Assert%2A> tam güven için (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), kritik bir sınıf örneği oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d218-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="5d218-162">(Derlemenizi hiçbir saydamlık işaretler sahip ve tamamen güvenilir olarak yüklenen her meydana gelir.) Bu nedenle, bu işlevle yalnızca güvendiğiniz kod oluşturmak dikkatli olmak zorunda ve yeni uygulama etki alanında yalnızca tam olarak güvenilen sınıfların örneklerini oluşturmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="5d218-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="5d218-163">Yeni bir etki alanında bir sınıfın bir örneğini oluşturmak için sınıf genişletmek sahip olduğuna dikkat edin <xref:System.MarshalByRefObject> sınıfı</span><span class="sxs-lookup"><span data-stu-id="5d218-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="5d218-164">Yeni etki alanı örneğe bir başvuru bu etki alanında sarmalamadan çıkarma.</span><span class="sxs-lookup"><span data-stu-id="5d218-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="5d218-165">Bu başvuru, güvenilmeyen kod yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d218-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="5d218-166">Çağrı `ExecuteUntrustedCode` örneğinde yöntemi `Sandboxer` oluşturduğunuz sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5d218-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="5d218-167">Bu çağrı, sınırlı izinlere sahip koruma alanlı uygulama etki alanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5d218-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is   
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <xref:System.Reflection> <span data-ttu-id="5d218-168">kısmen güvenilen bir derleme içinde bir yöntemin bir tanıtıcı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d218-168">is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="5d218-169">Tanıtıcı, en düşük izinleri ile güvenli bir şekilde kod yürütmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d218-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="5d218-170">Önceki kodda, Not <xref:System.Security.PermissionSet.Assert%2A> yazdırmadan önce tam güven izni <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="5d218-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="5d218-171">Genişletilmiş bilgileri elde etmek için kullanılan tam güven assert <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="5d218-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="5d218-172">Olmadan <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> yöntemi <xref:System.Security.SecurityException> yığında kısmen güvenilen kod olduğunu bulacak ve döndürülen bilgileri kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="5d218-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="5d218-173">Bu bilgiler, ancak bu riski azaltılabilir vermeyerek tarafından kısmi güven kodu okuyabilir, bu güvenlik sorunlarına neden olabileceği <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="5d218-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="5d218-174">Tam güven assert kullanılmamalıdır ve yalnızca, eminseniz, kısmi güven kodu için tam güven yükseltmesine izin.</span><span class="sxs-lookup"><span data-stu-id="5d218-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="5d218-175">Bir kural olarak, aynı işlevde ve tam güven için bir onay olarak adlandırılan sonra kod yazmadan çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="5d218-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="5d218-176">Assert kullanmayı bitirdiğinizde her zaman geri dönmek için iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="5d218-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d218-177">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d218-177">Example</span></span>  
 <span data-ttu-id="5d218-178">Aşağıdaki örnek, önceki bölümde yordamı uygular.</span><span class="sxs-lookup"><span data-stu-id="5d218-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="5d218-179">Örnekte, bir proje adlı `Sandboxer` Visual Studio'da Çözüm ayrıca adlı bir proje içeren `UntrustedCode`, sınıf uygulayan `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="5d218-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="5d218-180">Bu senaryo dönmesi beklenen bir yöntem içeren bir kitaplık derlemesine yüklediğiniz varsayılır `true` veya `false` sayı, Fibonacci sayı sağlanıp sağlanmadığını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="5d218-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="5d218-181">Bunun yerine, bilgisayarınızda bir dosyayı okumak yöntem çalışır.</span><span class="sxs-lookup"><span data-stu-id="5d218-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="5d218-182">Aşağıdaki örnek, güvenilmeyen kod gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d218-182">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="5d218-183">Aşağıdaki örnekte gösterildiği `Sandboxer` güvenilmeyen kod yürüten bir uygulama kodu.</span><span class="sxs-lookup"><span data-stu-id="5d218-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d218-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d218-184">See also</span></span>

- [<span data-ttu-id="5d218-185">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5d218-185">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
