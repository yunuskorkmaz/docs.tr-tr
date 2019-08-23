---
title: 'Nasıl yapılır: Bir korumalı alanda kısmen güvenilen kod Çalıştır'
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
ms.openlocfilehash: a439e02046e04d8628415237d6717a74b9922371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910942"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="f9534-102">Nasıl yapılır: Bir korumalı alanda kısmen güvenilen kod Çalıştır</span><span class="sxs-lookup"><span data-stu-id="f9534-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="f9534-103">Korumalı alana alma, kodu, koda verilen erişim izinlerini sınırlayan kısıtlı bir güvenlik ortamında çalıştırmaya yönelik bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="f9534-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="f9534-104">Örneğin, tam olarak güvenmediğiniz bir kaynaktan yönetilen bir kitaplığınız varsa, bunu tam güvenilir olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9534-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="f9534-105">Bunun yerine, kodu, izinlerini beklediğinizi (örneğin, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izin) sınırlayan bir korumalı alana yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9534-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="f9534-106">Ayrıca, dağıtmak istediğiniz kodu, kısmen güvenilen ortamlarda çalışacak şekilde test etmek için korumalı alana alma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9534-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="f9534-107"><xref:System.AppDomain> , Yönetilen uygulamalar için korumalı alan sağlamanın etkili bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="f9534-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="f9534-108">Kısmen güvenilen kodu çalıştırmak için kullanılan uygulama etki alanları, içinde <xref:System.AppDomain>çalışırken kullanılabilir olan korumalı kaynakları tanımlayan izinlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f9534-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="f9534-109">İçinde <xref:System.AppDomain> çalışan kod, <xref:System.AppDomain> ile ilişkili izinlerle ilişkilidir ve yalnızca belirtilen kaynaklara erişim izni verilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="f9534-110">Ayrıca <xref:System.AppDomain> , tam olarak <xref:System.Security.Policy.StrongName> güvenilir olarak yüklenecek derlemeleri tanımlamak için kullanılan bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="f9534-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="f9534-111">Bu, bir <xref:System.AppDomain> öğesinin, belirli yardımcı derlemelerin tam olarak güvenilir olmasını sağlayan yeni bir korumalı etki alanını başlatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9534-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="f9534-112">Derlemeleri tamamen güvenilir olarak yüklemek için başka bir seçenek de bunları genel derleme önbelleğine yerleştirmelidir; Ancak, derlemeleri bu bilgisayarda oluşturulan tüm uygulama etki alanlarında tam güvenilir olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="f9534-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="f9534-113">Tanımlayıcı adların listesi, daha kısıtlayıcı bir belirleme sağlayan<xref:System.AppDomain> kararların her birini destekler.</span><span class="sxs-lookup"><span data-stu-id="f9534-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="f9534-114">Bir korumalı alanda çalışan <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> uygulamalar için izin kümesini belirtmek üzere yöntem aşırı yüklemesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9534-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="f9534-115">Bu aşırı yükleme, istediğiniz kod erişimi güvenliğinin tam düzeyini belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9534-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="f9534-116">Bu aşırı yükleme kullanılarak bir <xref:System.AppDomain> öğesine yüklenen derlemeler yalnızca belirtilen izin kümesine sahip olabilir ya da tam güvenilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="f9534-117">Bütünleştirilmiş kod, genel derleme önbelleğidir veya `fullTrustAssemblies` <xref:System.Security.Policy.StrongName>() dizi parametresinde listeleniyorsa, tam güven verilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="f9534-118">Yalnızca tam güvenilir olarak bilinen derlemeler `fullTrustAssemblies` listeye eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f9534-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="f9534-119">Aşırı yükleme aşağıdaki imzaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f9534-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="f9534-120"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> Yöntem aşırı yüklemesi için parametreler,, için <xref:System.AppDomain> <xref:System.AppDomainSetup> kanıt, korumalı <xref:System.AppDomain>alan için uygulama temelini tanımlayan nesne, kullanılacak izin kümesi ve tanımlayıcı adlar belirler tam güvenilir derlemeler.</span><span class="sxs-lookup"><span data-stu-id="f9534-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="f9534-121">Güvenlik nedenleriyle, `info` parametresinde belirtilen uygulama tabanı, barındırma uygulaması için uygulama temeli olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9534-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="f9534-122">Parametresi için, açıkça oluşturduğunuz bir izin kümesini ya da <xref:System.Security.SecurityManager.GetStandardSandbox%2A> yöntemi tarafından oluşturulan standart bir izin kümesini belirtebilirsiniz. `grantSet`</span><span class="sxs-lookup"><span data-stu-id="f9534-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="f9534-123">Çoğu <xref:System.AppDomain> yüklerden farklı olarak, kısmen güvenilen <xref:System.AppDomain> derlemeler için izin kümesini belirlemede ( `securityInfo` parametresi tarafından sağlanır) için kanıt kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f9534-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="f9534-124">Bunun yerine, `grantSet` parametresi tarafından bağımsız olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="f9534-125">Ancak kanıt, yalıtılmış depolama kapsamını belirleme gibi başka amaçlar için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="f9534-126">Bir korumalı alanda uygulama çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f9534-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="f9534-127">Güvenilmeyen uygulamaya verilecek izin kümesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9534-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="f9534-128"><xref:System.Security.Permissions.SecurityPermissionFlag.Execution> İzin verdiğiniz en düşük izin izinidir.</span><span class="sxs-lookup"><span data-stu-id="f9534-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="f9534-129">Ayrıca, güvenilir olmayan kod için güvenli olabileceğini düşündüğünüz ek izinler verebilirsiniz; Örneğin, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="f9534-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="f9534-130">Aşağıdaki kod yalnızca <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> izne sahip yeni bir izin kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9534-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="f9534-131">Alternatif olarak, Internet gibi var olan bir adlandırılmış izin kümesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9534-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="f9534-132">Yöntemi <xref:System.Security.SecurityManager.GetStandardSandbox%2A> , kanıt içindeki bölgeye `Internet` bağlı olarak bir izin `LocalIntranet` kümesi veya bir izin kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9534-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="f9534-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>Ayrıca, başvuru olarak geçirilen bazı kanıt nesneleri için kimlik izinleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9534-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="f9534-134">Güvenilmeyen kodu çağıran barındırma sınıfını (Bu örnekte adlandırılır `Sandboxer` ) içeren derlemeyi imzalayın.</span><span class="sxs-lookup"><span data-stu-id="f9534-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="f9534-135"><xref:System.Security.Policy.StrongName> Derlemeyi çağrının<xref:System.AppDomain.CreateDomain%2A> parametresinin dizisine imzalamak için kullanılan öğesini ekleyin. <xref:System.Security.Policy.StrongName> `fullTrustAssemblies`</span><span class="sxs-lookup"><span data-stu-id="f9534-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="f9534-136">Barındırma sınıfının, kısmi güven kodunun yürütülmesini sağlamak veya kısmi güven uygulamasına hizmet sunmak için tam olarak güvenilir olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9534-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="f9534-137">Bu, <xref:System.Security.Policy.StrongName> bir derlemenin türünü okuduğunuzdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="f9534-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="f9534-138">Mscorlib ve System. dll gibi .NET Framework derlemelerin tam güven listesine eklenmesi gerekmez, çünkü genel derleme önbelleğinden tam güvenilir olarak yüklenirler.</span><span class="sxs-lookup"><span data-stu-id="f9534-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="f9534-139"><xref:System.AppDomain.CreateDomain%2A> Yönteminin <xref:System.AppDomainSetup> parametresini başlatın.</span><span class="sxs-lookup"><span data-stu-id="f9534-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="f9534-140">Bu parametreyle, yeni <xref:System.AppDomain>' nin birçok ayarını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9534-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="f9534-141">Özelliği önemli bir ayardır ve barındırma uygulamasının <xref:System.AppDomainSetup.ApplicationBase%2A> özelliğinden <xref:System.AppDomain> farklı olmalıdır. <xref:System.AppDomainSetup.ApplicationBase%2A></span><span class="sxs-lookup"><span data-stu-id="f9534-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="f9534-142"><xref:System.AppDomainSetup.ApplicationBase%2A> Ayarlar aynıysa, kısmi güven uygulaması, ana bilgisayar uygulamasının tanımladığı özel durumu (tam olarak güvenilir olarak) tarafından daha sonra onu kötüye yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="f9534-143">Bu, bir catch (özel durum) kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f9534-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="f9534-144">Konağın uygulama tabanının, korumalı uygulamanın uygulama tabanından farklı ayarlanması, yararlanma riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="f9534-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="f9534-145">Belirttiğimiz parametreleri kullanarak uygulama etki alanı oluşturmak için yöntemaşırıyüklemesiniçağırın.<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29></span><span class="sxs-lookup"><span data-stu-id="f9534-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="f9534-146">Bu yöntemin imzası:</span><span class="sxs-lookup"><span data-stu-id="f9534-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="f9534-147">Ek bilgiler:</span><span class="sxs-lookup"><span data-stu-id="f9534-147">Additional information:</span></span>  
  
    - <span data-ttu-id="f9534-148">Bu, <xref:System.AppDomain.CreateDomain%2A> yöntemi parametresi <xref:System.Security.PermissionSet> olarak alan tek aşırı yüktür ve bu nedenle kısmi güven ayarında bir uygulamayı yüklemenize imkan tanıyan tek aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="f9534-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="f9534-149">`evidence` Parametresi, bir izin kümesini hesaplamak için kullanılmaz; .NET Framework diğer özelliklerinin tanımlanması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9534-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="f9534-150">`info` Parametresinin özelliğinin ayarlanması bu aşırı yükleme için zorunludur. <xref:System.AppDomainSetup.ApplicationBase%2A></span><span class="sxs-lookup"><span data-stu-id="f9534-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="f9534-151">Parametresi, `params` anahtar sözcüğüne sahiptir, yani bir <xref:System.Security.Policy.StrongName> dizi oluşturmak için gerekli değildir. `fullTrustAssemblies`</span><span class="sxs-lookup"><span data-stu-id="f9534-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="f9534-152">Parametre olarak 0, 1 veya daha fazla tanımlayıcı ad geçirmek için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="f9534-153">Uygulama etki alanı oluşturma kodu:</span><span class="sxs-lookup"><span data-stu-id="f9534-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="f9534-154">Kodu oluşturduğunuz korumalı alana alma <xref:System.AppDomain> içine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f9534-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="f9534-155">Bu, iki şekilde yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="f9534-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="f9534-156">Derleme için <xref:System.AppDomain.ExecuteAssembly%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="f9534-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="f9534-157"><xref:System.Activator.CreateInstanceFrom%2A> Yeni <xref:System.MarshalByRefObject> içinde türetilmiş bir sınıfın örneğini oluşturmak için yöntemini kullanın. <xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="f9534-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="f9534-158">İkinci yöntem tercih edilir, çünkü parametreleri yeni <xref:System.AppDomain> örneğe geçirmek daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f9534-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="f9534-159"><xref:System.Activator.CreateInstanceFrom%2A> Yöntemi iki önemli özellik sağlar:</span><span class="sxs-lookup"><span data-stu-id="f9534-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="f9534-160">Derlemenizi içermeyen bir konuma işaret eden bir kod tabanı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9534-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="f9534-161">Bir <xref:System.Security.CodeAccessPermission.Assert%2A> kritik sınıfın örneğini oluşturmanızı sağlayan tam güven (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>) için oluşturma ' yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9534-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="f9534-162">(Bu, derlemenizin saydamlık işaretlerini yoksa ve tamamen güvenilir olarak yüklendiğinde gerçekleşir.) Bu nedenle, yalnızca bu işlevle güvendiğiniz kodu oluşturmak için dikkatli olmanız gerekir ve yeni uygulama etki alanında yalnızca tam olarak güvenilen sınıfların örneklerini oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="f9534-163">Yeni bir etki alanında sınıfın bir örneğini oluşturmak için sınıfın <xref:System.MarshalByRefObject> sınıfı genişletmesine sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f9534-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="f9534-164">Yeni etki alanı örneğinin bu etki alanındaki bir başvuruya sarmalaması geri alınıyor.</span><span class="sxs-lookup"><span data-stu-id="f9534-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="f9534-165">Bu başvuru güvenilmeyen kodu yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9534-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="f9534-166">Yeni oluşturduğunuz `Sandboxer` sınıfın örneğindeki yöntemiçağırın.`ExecuteUntrustedCode`</span><span class="sxs-lookup"><span data-stu-id="f9534-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="f9534-167">Bu çağrı, sınırlı izinlere sahip olan korumalı uygulama etki alanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f9534-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
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
  
     <span data-ttu-id="f9534-168"><xref:System.Reflection>kısmen güvenilen derlemedeki bir yöntemin tanıtıcısını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9534-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="f9534-169">Tanıtıcı, kodu minimum izinlerle güvenli bir şekilde yürütmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="f9534-170">Önceki kodda, ' yi <xref:System.Security.PermissionSet.Assert%2A> <xref:System.Security.SecurityException>yazdırmadan önce tam güven izni için ' a göz önüne alın.</span><span class="sxs-lookup"><span data-stu-id="f9534-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="f9534-171">Tam güven onayı, <xref:System.Security.SecurityException>' dan genişletilmiş bilgileri elde etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f9534-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="f9534-172"><xref:System.Security.PermissionSet.Assert%2A> Olmadan<xref:System.Security.SecurityException.ToString%2A> yöntemi ,<xref:System.Security.SecurityException> yığın üzerinde kısmen güvenilen kod olduğunu ve döndürülen bilgileri kısıtlayamayacağını keşfeder.</span><span class="sxs-lookup"><span data-stu-id="f9534-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="f9534-173">Kısmi güven kodu bu bilgileri okuyabiliyorsanız ve risk verilmemesine <xref:System.Security.Permissions.UIPermission>göre azaltıldığında, bu güvenlik sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9534-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="f9534-174">Tam güven onayı, az önce ve yalnızca kısmi güven kodunun tam güvene yükseltilmesine izin vermediğinizden emin olduğunuzda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9534-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="f9534-175">Kural olarak, aynı işlevde güvenmediğiniz ve tam güven için bir onay çağırdıktan sonra kodu çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="f9534-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="f9534-176">Kullanmayı bitirdikten sonra her zaman onayı döndürmenizde iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="f9534-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9534-177">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9534-177">Example</span></span>  
 <span data-ttu-id="f9534-178">Aşağıdaki örnek, önceki bölümde yordamı uygular.</span><span class="sxs-lookup"><span data-stu-id="f9534-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="f9534-179">Örnekte, Visual Studio çözümünde adlı `Sandboxer` bir proje, sınıfını `UntrustedClass`uygulayan adlı `UntrustedCode`bir projeyi de içerir.</span><span class="sxs-lookup"><span data-stu-id="f9534-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="f9534-180">Bu senaryoda, döndürmesi `true` beklenen bir yöntemi içeren bir kitaplık derlemesini indirdiğiniz veya `false` girdiğiniz sayının bir fibonaccı numarası olup olmadığını belirtmesi gerektiğini varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9534-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="f9534-181">Bunun yerine, yöntemi bilgisayarınızdan bir dosyayı okumaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="f9534-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="f9534-182">Aşağıdaki örnek güvenilmeyen kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9534-182">The following example shows the untrusted code.</span></span>  
  
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
  
 <span data-ttu-id="f9534-183">Aşağıdaki örnek, güvenilmeyen kodu `Sandboxer` yürüten uygulama kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9534-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9534-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9534-184">See also</span></span>

- [<span data-ttu-id="f9534-185">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f9534-185">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
