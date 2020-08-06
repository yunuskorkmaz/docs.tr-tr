---
title: 'Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma'
description: .NET 'teki bir korumalı alanda kısmen güvenilen kodun nasıl çalıştırılacağını öğrenin. AppDomain sınıfı korumalı alana alma yönetilen uygulamaların etkin bir yoludur.
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: 415a42f7c4f4866bb72f19bdd6f02bfdb5158bf8
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855809"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="ac8fa-104">Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ac8fa-104">How to: Run Partially Trusted Code in a Sandbox</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="ac8fa-105">Korumalı alana alma, kodu, koda verilen erişim izinlerini sınırlayan kısıtlı bir güvenlik ortamında çalıştırmaya yönelik bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-105">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="ac8fa-106">Örneğin, tam olarak güvenmediğiniz bir kaynaktan yönetilen bir kitaplığınız varsa, bunu tam güvenilir olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-106">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="ac8fa-107">Bunun yerine, kodu, izinlerini beklediğinizi (örneğin, izin) sınırlayan bir korumalı alana yerleştirmeniz gerekir <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-107">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="ac8fa-108">Ayrıca, dağıtmak istediğiniz kodu, kısmen güvenilen ortamlarda çalışacak şekilde test etmek için korumalı alana alma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-108">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="ac8fa-109"><xref:System.AppDomain>, Yönetilen uygulamalar için korumalı alan sağlamanın etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-109">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="ac8fa-110">Kısmen güvenilen kodu çalıştırmak için kullanılan uygulama etki alanları, içinde çalışırken kullanılabilir olan korumalı kaynakları tanımlayan izinlere sahiptir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-110">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="ac8fa-111">İçinde çalışan kod, <xref:System.AppDomain> ile ilişkili izinlerle ilişkilidir <xref:System.AppDomain> ve yalnızca belirtilen kaynaklara erişim izni verilir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-111">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="ac8fa-112"><xref:System.AppDomain>Ayrıca, <xref:System.Security.Policy.StrongName> tam olarak güvenilir olarak yüklenecek derlemeleri tanımlamak için kullanılan bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-112">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="ac8fa-113">Bu, bir öğesinin, <xref:System.AppDomain> belirli yardımcı derlemelerin tam olarak güvenilir olmasını sağlayan yeni bir korumalı etki alanını başlatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-113">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="ac8fa-114">Derlemeleri tamamen güvenilir olarak yüklemek için başka bir seçenek de bunları genel derleme önbelleğine yerleştirmelidir; Ancak, derlemeleri bu bilgisayarda oluşturulan tüm uygulama etki alanlarında tam güvenilir olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-114">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="ac8fa-115">Tanımlayıcı adların listesi, <xref:System.AppDomain> daha kısıtlayıcı bir belirleme sağlayan kararların her birini destekler.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-115">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="ac8fa-116"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>Bir korumalı alanda çalışan uygulamalar için izin kümesini belirtmek üzere yöntem aşırı yüklemesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-116">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="ac8fa-117">Bu aşırı yükleme, istediğiniz kod erişimi güvenliğinin tam düzeyini belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-117">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="ac8fa-118"><xref:System.AppDomain>Bu aşırı yükleme kullanılarak bir öğesine yüklenen derlemeler yalnızca belirtilen izin kümesine sahip olabilir ya da tam güvenilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-118">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="ac8fa-119">Bütünleştirilmiş kod, genel derleme önbelleğidir veya `fullTrustAssemblies` () dizi parametresinde listeleniyorsa, tam güven verilir <xref:System.Security.Policy.StrongName> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-119">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="ac8fa-120">Yalnızca tam güvenilir olarak bilinen derlemeler `fullTrustAssemblies` listeye eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-120">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="ac8fa-121">Aşırı yükleme aşağıdaki imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ac8fa-121">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="ac8fa-122">Yöntem aşırı yüklemesi için parametreler,, <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> <xref:System.AppDomain> için kanıt, <xref:System.AppDomain> <xref:System.AppDomainSetup> korumalı alan için uygulama temelini tanımlayan nesne, kullanılacak izin kümesi ve tam güvenilir derlemeler için tanımlayıcı adlar belirler.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-122">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="ac8fa-123">Güvenlik nedenleriyle, parametresinde belirtilen uygulama tabanı, `info` barındırma uygulaması için uygulama temeli olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-123">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="ac8fa-124">Parametresi için `grantSet` , açıkça oluşturduğunuz bir izin kümesini ya da yöntemi tarafından oluşturulan standart bir izin kümesini belirtebilirsiniz <xref:System.Security.SecurityManager.GetStandardSandbox%2A> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-124">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="ac8fa-125">Çoğu <xref:System.AppDomain> yüklerden farklı olarak, <xref:System.AppDomain> `securityInfo` kısmen güvenilen derlemeler için izin kümesini belirlemede (parametresi tarafından sağlanır) için kanıt kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-125">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="ac8fa-126">Bunun yerine, parametresi tarafından bağımsız olarak belirtilir `grantSet` .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-126">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="ac8fa-127">Ancak kanıt, yalıtılmış depolama kapsamını belirleme gibi başka amaçlar için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-127">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="ac8fa-128">Bir korumalı alanda uygulama çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ac8fa-128">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="ac8fa-129">Güvenilmeyen uygulamaya verilecek izin kümesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-129">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="ac8fa-130">İzin verdiğiniz en düşük izin <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izinidir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-130">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="ac8fa-131">Ayrıca, güvenilir olmayan kod için güvenli olabileceğini düşündüğünüz ek izinler verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-131">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="ac8fa-132">Aşağıdaki kod yalnızca izne sahip yeni bir izin kümesi oluşturur <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-132">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="ac8fa-133">Alternatif olarak, Internet gibi var olan bir adlandırılmış izin kümesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-133">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="ac8fa-134"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>Yöntemi, `Internet` `LocalIntranet` kanıt içindeki bölgeye bağlı olarak bir izin kümesi veya bir izin kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-134">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="ac8fa-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>Ayrıca, başvuru olarak geçirilen bazı kanıt nesneleri için kimlik izinleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-135"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="ac8fa-136">Güvenilmeyen kodu çağıran barındırma sınıfını (Bu örnekte adlandırılır) içeren derlemeyi imzalayın `Sandboxer` .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-136">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="ac8fa-137"><xref:System.Security.Policy.StrongName>Derlemeyi <xref:System.Security.Policy.StrongName> çağrının parametresinin dizisine imzalamak için kullanılan öğesini ekleyin `fullTrustAssemblies` <xref:System.AppDomain.CreateDomain%2A> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-137">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="ac8fa-138">Barındırma sınıfının, kısmi güven kodunun yürütülmesini sağlamak veya kısmi güven uygulamasına hizmet sunmak için tam olarak güvenilir olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-138">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="ac8fa-139">Bu, <xref:System.Security.Policy.StrongName> bir derlemenin türünü okuduğunuzdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="ac8fa-139">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="ac8fa-140">Mscorlib ve System.dll gibi .NET Framework derlemelerin tam güven listesine eklenmesi gerekmez, çünkü genel derleme önbelleğinden tam güvenilir olarak yüklenirler.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-140">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="ac8fa-141"><xref:System.AppDomainSetup>Yönteminin parametresini başlatın <xref:System.AppDomain.CreateDomain%2A> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-141">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="ac8fa-142">Bu parametreyle, yeni ' nin birçok ayarını kontrol edebilirsiniz <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-142">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="ac8fa-143"><xref:System.AppDomainSetup.ApplicationBase%2A>Özelliği önemli bir ayardır ve <xref:System.AppDomainSetup.ApplicationBase%2A> barındırma uygulamasının özelliğinden farklı olmalıdır <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-143">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="ac8fa-144"><xref:System.AppDomainSetup.ApplicationBase%2A>Ayarlar aynıysa, kısmi güven uygulaması, ana bilgisayar uygulamasının tanımladığı özel durumu (tam olarak güvenilir olarak) tarafından daha sonra onu kötüye yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-144">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="ac8fa-145">Bu, bir catch (özel durum) kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-145">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="ac8fa-146">Konağın uygulama tabanının, korumalı uygulamanın uygulama tabanından farklı ayarlanması, yararlanma riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-146">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="ac8fa-147"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29>Belirttiğimiz parametreleri kullanarak uygulama etki alanı oluşturmak için yöntem aşırı yüklemesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-147">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="ac8fa-148">Bu yöntemin imzası:</span><span class="sxs-lookup"><span data-stu-id="ac8fa-148">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="ac8fa-149">Ek bilgiler:</span><span class="sxs-lookup"><span data-stu-id="ac8fa-149">Additional information:</span></span>  
  
    - <span data-ttu-id="ac8fa-150">Bu, <xref:System.AppDomain.CreateDomain%2A> yöntemi parametresi olarak alan tek aşırı <xref:System.Security.PermissionSet> yüktür ve bu nedenle kısmi güven ayarında bir uygulamayı yüklemenize imkan tanıyan tek aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-150">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="ac8fa-151">`evidence`Parametresi, bir izin kümesini hesaplamak için kullanılmaz; .NET Framework diğer özelliklerinin tanımlanması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-151">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="ac8fa-152"><xref:System.AppDomainSetup.ApplicationBase%2A>Parametresinin özelliğinin ayarlanması `info` Bu aşırı yükleme için zorunludur.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-152">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="ac8fa-153">`fullTrustAssemblies`Parametresi, `params` anahtar sözcüğüne sahiptir, yani bir dizi oluşturmak için gerekli değildir <xref:System.Security.Policy.StrongName> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-153">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="ac8fa-154">Parametre olarak 0, 1 veya daha fazla tanımlayıcı ad geçirmek için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-154">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="ac8fa-155">Uygulama etki alanı oluşturma kodu:</span><span class="sxs-lookup"><span data-stu-id="ac8fa-155">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="ac8fa-156">Kodu oluşturduğunuz korumalı alana alma içine yükleyin <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-156">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="ac8fa-157">Bu, iki şekilde yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="ac8fa-157">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="ac8fa-158"><xref:System.AppDomain.ExecuteAssembly%2A>Derleme için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-158">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="ac8fa-159"><xref:System.Activator.CreateInstanceFrom%2A>Yeni içinde türetilmiş bir sınıfın örneğini oluşturmak için yöntemini kullanın <xref:System.MarshalByRefObject> <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-159">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="ac8fa-160">İkinci yöntem tercih edilir, çünkü parametreleri yeni örneğe geçirmek daha kolay hale getirir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-160">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="ac8fa-161"><xref:System.Activator.CreateInstanceFrom%2A>Yöntemi iki önemli özellik sağlar:</span><span class="sxs-lookup"><span data-stu-id="ac8fa-161">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="ac8fa-162">Derlemenizi içermeyen bir konuma işaret eden bir kod tabanı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-162">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="ac8fa-163">Bir <xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType> kritik sınıfın örneğini oluşturmanızı sağlayan tam güven () için oluşturma ' yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-163">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="ac8fa-164">(Bu, derlemenizin saydamlık işaretlerini yoksa ve tamamen güvenilir olarak yüklendiğinde gerçekleşir.) Bu nedenle, yalnızca bu işlevle güvendiğiniz kodu oluşturmak için dikkatli olmanız gerekir ve yeni uygulama etki alanında yalnızca tam olarak güvenilen sınıfların örneklerini oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-164">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="ac8fa-165">Yeni bir etki alanındaki sınıfın bir örneğini oluşturmak için, sınıfı sınıfını genişletmelidir <xref:System.MarshalByRefObject> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-165">To create an instance of a class in a new domain, the class must extend the <xref:System.MarshalByRefObject> class.</span></span>
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="ac8fa-166">Yeni etki alanı örneğinin bu etki alanındaki bir başvuruya sarmalaması geri alınıyor.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-166">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="ac8fa-167">Bu başvuru güvenilmeyen kodu yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-167">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="ac8fa-168">`ExecuteUntrustedCode` `Sandboxer` Yeni oluşturduğunuz sınıfın örneğindeki yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-168">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="ac8fa-169">Bu çağrı, sınırlı izinlere sahip olan korumalı uygulama etki alanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-169">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
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
  
     <span data-ttu-id="ac8fa-170"><xref:System.Reflection>kısmen güvenilen derlemedeki bir yöntemin tanıtıcısını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-170"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="ac8fa-171">Tanıtıcı, kodu minimum izinlerle güvenli bir şekilde yürütmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-171">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="ac8fa-172">Önceki kodda, ' yi <xref:System.Security.PermissionSet.Assert%2A> yazdırmadan önce tam güven izni için ' a göz önüne alın <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-172">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="ac8fa-173">Tam güven onayı, ' dan genişletilmiş bilgileri elde etmek için kullanılır <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-173">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="ac8fa-174">Olmadan <xref:System.Security.PermissionSet.Assert%2A> <xref:System.Security.SecurityException.ToString%2A> yöntemi, <xref:System.Security.SecurityException> yığın üzerinde kısmen güvenilen kod olduğunu ve döndürülen bilgileri kısıtlayamayacağını keşfeder.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-174">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="ac8fa-175">Kısmi güven kodu bu bilgileri okuyabiliyorsanız ve risk verilmemesine göre azaltıldığında, bu güvenlik sorunlarına neden olabilir <xref:System.Security.Permissions.UIPermission> .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-175">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="ac8fa-176">Tam güven onayı, az önce ve yalnızca kısmi güven kodunun tam güvene yükseltilmesine izin vermediğinizden emin olduğunuzda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-176">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="ac8fa-177">Kural olarak, aynı işlevde güvenmediğiniz ve tam güven için bir onay çağırdıktan sonra kodu çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-177">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="ac8fa-178">Kullanmayı bitirdikten sonra her zaman onayı döndürmenizde iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-178">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac8fa-179">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac8fa-179">Example</span></span>  
 <span data-ttu-id="ac8fa-180">Aşağıdaki örnek, önceki bölümde yordamı uygular.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-180">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="ac8fa-181">Örnekte, `Sandboxer` Visual Studio çözümünde adlı bir proje, sınıfını uygulayan adlı bir projeyi de içerir `UntrustedCode` `UntrustedClass` .</span><span class="sxs-lookup"><span data-stu-id="ac8fa-181">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="ac8fa-182">Bu senaryoda, döndürmesi beklenen bir yöntemi içeren bir kitaplık derlemesini indirdiğiniz `true` veya `false` girdiğiniz sayının bir Fibonaccı numarası olup olmadığını belirtmesi gerektiğini varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-182">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="ac8fa-183">Bunun yerine, yöntemi bilgisayarınızdan bir dosyayı okumaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-183">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="ac8fa-184">Aşağıdaki örnek güvenilmeyen kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-184">The following example shows the untrusted code.</span></span>  
  
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
  
 <span data-ttu-id="ac8fa-185">Aşağıdaki örnek, `Sandboxer` Güvenilmeyen kodu yürüten uygulama kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-185">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac8fa-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac8fa-186">See also</span></span>

- [<span data-ttu-id="ac8fa-187">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ac8fa-187">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
