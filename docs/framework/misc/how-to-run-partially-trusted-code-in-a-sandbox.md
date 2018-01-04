---
title: "Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc335bfef4993f6e730dca93cd645d886a9d13b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="0484d-102">Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0484d-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="0484d-103">Korumalı alan kodu için kod erişim izinleri sınırlayan kısıtlı güvenlik ortamı çalışan uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="0484d-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="0484d-104">Yönetilen bir kitaplık tamamen güvenmediğiniz bir kaynaktan varsa, örneğin, onu tam olarak güvenilir olarak çalıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0484d-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="0484d-105">Bunun yerine, izinlerini gerek beklediğiniz bu sınırlar bir korumalı alanı içinde kodu yerleştirmeniz (örneğin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni).</span><span class="sxs-lookup"><span data-stu-id="0484d-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="0484d-106">Korumalı alan, kısmen güvenilen ortamlarında çalışır, dağıtma kodu test etmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0484d-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="0484d-107">Bir <xref:System.AppDomain> bir korumalı alan yönetilen uygulamaları için sağlama etkili bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="0484d-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="0484d-108">Kısmen güvenilen kod çalıştırmak için kullanılan uygulama etki alanları, içinde çalışırken kullanılabilir korunan kaynakları tanımlayan izinleriniz <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0484d-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="0484d-109">İçinde çalışan kod <xref:System.AppDomain> ilişkili izinler tarafından bağlı <xref:System.AppDomain> ve yalnızca belirtilen kaynakları erişmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="0484d-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="0484d-110"><xref:System.AppDomain> De içeren bir <xref:System.Security.Policy.StrongName> tam olarak güvenilir olarak yüklenmiş olması gerektiğini derlemeleri tanımlamak için kullanılan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="0484d-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="0484d-111">Oluşturucusu, böylece bir <xref:System.AppDomain> tam olarak güvenilir olması belirli yardımcı derlemeler izin veren yeni bir korumalı etki alanı başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="0484d-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="0484d-112">Derlemeleri tam olarak yükleme için başka bir güvenilen genel derleme önbelleğinde yerleştirmek için bir seçenektir; Ancak, bu bilgisayarda oluşturulan tüm uygulama etki alanlarında derlemeleri tam güvenilir olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="0484d-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="0484d-113">Güçlü listesini destekler adları bir başına-<xref:System.AppDomain> sağlayan daha kısıtlayıcı belirleme kararı.</span><span class="sxs-lookup"><span data-stu-id="0484d-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="0484d-114">Kullanabileceğiniz <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> izni belirtmek için yöntemi aşırı yüklemesini ayarlamak korumalı alanda çalışan uygulamalar için.</span><span class="sxs-lookup"><span data-stu-id="0484d-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="0484d-115">Bu aşırı istediğiniz kod erişim güvenliği tam düzeyini belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0484d-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="0484d-116">İçine yüklenmiş derlemeleri bir <xref:System.AppDomain> Bu aşırı kullanarak ya da sahip olabilirsiniz belirtilen kümesi yalnızca verin veya tam güvenilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="0484d-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="0484d-117">Derleme genel derleme önbelleğinde ise tam güven veya listelenen verilir `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) dizi parametresi.</span><span class="sxs-lookup"><span data-stu-id="0484d-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="0484d-118">Yalnızca tam güvenilir olduğu bilinen derlemeler için eklenmesi `fullTrustAssemblies` listesi.</span><span class="sxs-lookup"><span data-stu-id="0484d-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="0484d-119">Aşırı aşağıdaki imzası vardır:</span><span class="sxs-lookup"><span data-stu-id="0484d-119">The overload has the following signature:</span></span>  
  
```  
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="0484d-120">Parametrelerini <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> yöntemi aşırı yüklemesini belirtin adını <xref:System.AppDomain>, kanıt için <xref:System.AppDomain>, <xref:System.AppDomainSetup> korumalı alan, kullanmak üzere ayarlanmış izni ve güçlü adlar uygulama temel tanımlayan nesne tam güvenilir derlemeler.</span><span class="sxs-lookup"><span data-stu-id="0484d-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="0484d-121">Uygulama temel güvenlik nedeniyle, belirtilen `info` parametresi barındırma uygulama için temel uygulama olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0484d-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="0484d-122">İçin `grantSet` parametresini açıkça oluşturulan bir izin kümesi veya standart izin belirtebilirsiniz kümesi tarafından oluşturulan <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0484d-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="0484d-123">Çoğu aksine <xref:System.AppDomain> yükler, kanıt için <xref:System.AppDomain> (tarafından sağlanan `securityInfo` parametresi) kısmen güvenilir derlemeler için ayarlanmış grant belirlemek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="0484d-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="0484d-124">Bunun yerine, bu bağımsız olarak tarafından belirtilen `grantSet` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0484d-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="0484d-125">Ancak, kanıt yalıtılmış depolama kapsamı belirleme gibi diğer amaçlar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0484d-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="0484d-126">Korumalı alanda bir uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0484d-126">To run an application in a sandbox</span></span>  
  
1.  <span data-ttu-id="0484d-127">Güvenilmeyen uygulamaya verilebilmesi için izni oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0484d-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="0484d-128">Vermek en az izni <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni.</span><span class="sxs-lookup"><span data-stu-id="0484d-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="0484d-129">Ayrıca, ek izinler düşündüğünüz güvenilmeyen kod için güvenli verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="0484d-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="0484d-130">Aşağıdaki kod yalnızca kümesiyle yeni bir izin oluşturur <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izni.</span><span class="sxs-lookup"><span data-stu-id="0484d-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```  
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="0484d-131">Alternatif olarak, Internet gibi mevcut bir adlandırılmış izin kümesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0484d-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="0484d-132"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> Yöntemi döndürür ya da bir `Internet` izin kümesi veya `LocalIntranet` izni kanıt bölge bağlı olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="0484d-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="0484d-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>Ayrıca bazı başvuru olarak geçirilen kanıt nesneler kimlik izinlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0484d-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2.  <span data-ttu-id="0484d-134">Barındırma sınıfı içeren bütünleştirilmiş kodun oturum (adlı `Sandboxer` Bu örnekte) güvenilmeyen kod çağırır.</span><span class="sxs-lookup"><span data-stu-id="0484d-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="0484d-135">Ekleme <xref:System.Security.Policy.StrongName> derlemeye imzalamak için kullanılan <xref:System.Security.Policy.StrongName> dizisi `fullTrustAssemblies` parametresinin <xref:System.AppDomain.CreateDomain%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="0484d-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="0484d-136">Barındırma sınıfı çalıştırmalısınız, kısmi güven kodunun yürütülmesini etkinleştirmek veya kısmi güven uygulama hizmet sunmak için tam olarak güvenilir olarak.</span><span class="sxs-lookup"><span data-stu-id="0484d-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="0484d-137">Nasıl okuma budur <xref:System.Security.Policy.StrongName> derleme:</span><span class="sxs-lookup"><span data-stu-id="0484d-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```  
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="0484d-138">Mscorlib ve System.dll gibi .NET framework derlemeleri genel derleme önbelleğinden tam olarak güvenilir olarak yüklenen oldukları için tam güven listesine eklenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0484d-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3.  <span data-ttu-id="0484d-139">Initialize <xref:System.AppDomainSetup> parametresinin <xref:System.AppDomain.CreateDomain%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0484d-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="0484d-140">Yeni ayarların çoğu denetim bu parametreyle <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0484d-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="0484d-141"><xref:System.AppDomainSetup.ApplicationBase%2A> Özelliği önemli bir ayardır ve farklı olmalıdır <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği için <xref:System.AppDomain> barındırma uygulamasının.</span><span class="sxs-lookup"><span data-stu-id="0484d-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="0484d-142">Varsa <xref:System.AppDomainSetup.ApplicationBase%2A> ayarların aynı olduğundan, kısmi güven uygulama (tam olarak güvenilen) bir özel durum, tanımlar, böylece yararlanmasını yüklemek için barındırma uygulama elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0484d-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="0484d-143">Neden bir catch (özel) önerilmez başka bir neden de budur.</span><span class="sxs-lookup"><span data-stu-id="0484d-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="0484d-144">Uygulama ayarı korumalı uygulamanın uygulama temel konaktan farklı tabanı açıkları riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="0484d-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```  
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  <span data-ttu-id="0484d-145">Çağrı <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> belirtilen parametreleri kullanarak uygulama etki alanı oluşturmak için yöntemi aşırı yüklemesini.</span><span class="sxs-lookup"><span data-stu-id="0484d-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="0484d-146">Bu yöntem için imza şöyledir:</span><span class="sxs-lookup"><span data-stu-id="0484d-146">The signature for this method is:</span></span>  
  
    ```  
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="0484d-147">Ek bilgiler:</span><span class="sxs-lookup"><span data-stu-id="0484d-147">Additional information:</span></span>  
  
    -   <span data-ttu-id="0484d-148">Bu, yalnızca aşırı yüklemesi, <xref:System.AppDomain.CreateDomain%2A> yönteminin alan bir <xref:System.Security.PermissionSet> bir kısmi güven ayarı uygulamada bir parametre ve böylece olanak sağlayan yalnızca aşırı yük.</span><span class="sxs-lookup"><span data-stu-id="0484d-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    -   <span data-ttu-id="0484d-149">`evidence` Parametresi bir izin kümesi hesaplamak için kullanılan değil; tanımlama için .NET Framework'ün diğer özellikler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0484d-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="0484d-150">Ayarı <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği `info` için bu aşırı parametresi zorunludur.</span><span class="sxs-lookup"><span data-stu-id="0484d-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    -   <span data-ttu-id="0484d-151">`fullTrustAssemblies` Parametresine sahip `params` oluşturmak için gerekli olmadığı anlamına gelir anahtar sözcüğü bir <xref:System.Security.Policy.StrongName> dizi.</span><span class="sxs-lookup"><span data-stu-id="0484d-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="0484d-152">0, 1 veya daha fazla tanımlayıcı adlar parametre olarak geçirme izin verilir.</span><span class="sxs-lookup"><span data-stu-id="0484d-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    -   <span data-ttu-id="0484d-153">Uygulama etki alanı oluşturmak için kodu verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0484d-153">The code to create the application domain is:</span></span>  
  
    ```  
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  <span data-ttu-id="0484d-154">Korumalı alan kod yüklenemiyor <xref:System.AppDomain> oluşturduğunuz.</span><span class="sxs-lookup"><span data-stu-id="0484d-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="0484d-155">Bu iki yolla yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="0484d-155">This can be done in two ways:</span></span>  
  
    -   <span data-ttu-id="0484d-156">Çağrı <xref:System.AppDomain.ExecuteAssembly%2A> derleme için yöntem.</span><span class="sxs-lookup"><span data-stu-id="0484d-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    -   <span data-ttu-id="0484d-157">Kullanım <xref:System.Activator.CreateInstanceFrom%2A> sınıfının bir örneği oluşturmak için yöntemi türetilen <xref:System.MarshalByRefObject> yeni <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0484d-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="0484d-158">Yeni parametreleri kolaylaştırır ikinci yöntem tercih, çünkü <xref:System.AppDomain> örneği.</span><span class="sxs-lookup"><span data-stu-id="0484d-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="0484d-159"><xref:System.Activator.CreateInstanceFrom%2A> Yöntemi iki önemli özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="0484d-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    -   <span data-ttu-id="0484d-160">Derlemenizi içermeyen bir konuma işaret eden bir kod temeli kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0484d-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    -   <span data-ttu-id="0484d-161">Oluşturma altında yapabileceğiniz bir <xref:System.Security.CodeAccessPermission.Assert%2A> tam güven için (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), kritik sınıfının bir örneği oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0484d-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="0484d-162">(Derlemenizi hiçbir saydamlık işaretler varsa ve tam olarak güvenilir olarak yüklü olduğu her meydana gelir.) Bu nedenle, bu işlev yalnızca güvendiğiniz kodu oluşturmak dikkatli olmak zorunda ve yeni uygulama etki alanında yalnızca tam olarak güvenilmeyen sınıfların örnekleri oluşturmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="0484d-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```  
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="0484d-163">Yeni bir etki alanı sınıfının bir örneği oluşturmak için sınıfı genişletmek sahip olduğuna dikkat edin <xref:System.MarshalByRefObject> sınıfı</span><span class="sxs-lookup"><span data-stu-id="0484d-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```  
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  <span data-ttu-id="0484d-164">Bu etki alanındaki bir başvuru yeni etki alanı örneğine açılacak.</span><span class="sxs-lookup"><span data-stu-id="0484d-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="0484d-165">Bu başvuru, güvenilmeyen kod yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0484d-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```  
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  <span data-ttu-id="0484d-166">Çağrı `ExecuteUntrustedCode` örneğini yönteminde `Sandboxer` oluşturduğunuz sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0484d-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```  
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="0484d-167">Bu çağrı, sınırlı izinlere sahip korumalı uygulama etki alanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0484d-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```  
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
                (new PermissionSet(PermissionState.Unrestricted)).Assert();  
                Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
    CodeAccessPermission.RevertAssert();  
                Console.ReadLine();  
            }  
        }  
    ```  
  
     <span data-ttu-id="0484d-168"><xref:System.Reflection>kısmen güvenilen bütünleştirilmiş kodunda bir yöntem tanıtıcısı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0484d-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="0484d-169">Tanıtıcı minimum izinleri ile güvenli bir şekilde kod yürütmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0484d-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="0484d-170">Önceki kodda Not <xref:System.Security.PermissionSet.Assert%2A> yazdırma önce tam güven izni <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="0484d-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```  
    new PermissionSet(PermissionState.Unrestricted)).Assert()  
    ```  
  
     <span data-ttu-id="0484d-171">Tam güven assert genişletilmiş bilgileri elde etmek için kullanılan <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="0484d-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="0484d-172">Olmadan <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> yöntemi <xref:System.Security.SecurityException> yığında kısmen güvenilen kod olduğunu keşfeder ve dönen bilgiyi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="0484d-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="0484d-173">Kısmi güven kodunun bu bilgileri, ancak riski getirdiği değil vererek okuyabilir, bu güvenlik sorunlarına neden olabileceği <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="0484d-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="0484d-174">Tam güven assert olabildiğince az kullanılmalıdır ve yalnızca, eminseniz, tam güven yükseltmesine kısmi güven kodunun izin.</span><span class="sxs-lookup"><span data-stu-id="0484d-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="0484d-175">Bir kural olarak, aynı işlevde ve assert için tam güven adlı sonra güvenmediğiniz kod çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="0484d-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="0484d-176">Bunu kullanmayı bitirdikten sonra her zaman assert dönmek için iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="0484d-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0484d-177">Örnek</span><span class="sxs-lookup"><span data-stu-id="0484d-177">Example</span></span>  
 <span data-ttu-id="0484d-178">Aşağıdaki örnek yordam önceki bölümde uygular.</span><span class="sxs-lookup"><span data-stu-id="0484d-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="0484d-179">Örnekte, bir proje adlı `Sandboxer` Visual Studio'da Çözüm ayrıca adlı bir proje içeren `UntrustedCode`, sınıf uygulayan `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="0484d-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="0484d-180">Bu senaryo döndürmek için beklenen bir yöntem içeren Kitaplık derlemesi indirmiş varsayar `true` veya `false` sayı Fibonacci sayı sağladığınız olup olmadığını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="0484d-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="0484d-181">Bunun yerine, yöntemi, bir dosyayı bilgisayarınızdan okumaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="0484d-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="0484d-182">Aşağıdaki örnek, güvenilmeyen kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0484d-182">The following example shows the untrusted code.</span></span>  
  
```  
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
  
 <span data-ttu-id="0484d-183">Aşağıdaki örnekte gösterildiği `Sandboxer` güvenilmeyen kodu yürütür uygulama kodu.</span><span class="sxs-lookup"><span data-stu-id="0484d-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```  
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
            (new PermissionSet(PermissionState.Unrestricted)).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0484d-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0484d-184">See Also</span></span>  
 [<span data-ttu-id="0484d-185">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0484d-185">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
