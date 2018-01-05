---
title: "Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e5c57927a455b5d2a253becac35b1bf9033933f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="71749-102">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="71749-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="71749-103">Kullanmadan önce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet bilinen adı yazılı sözleşme ile COM uygulama içinde gerekli öznitelikli türleri COM ile kaydetme ve COM uygulama ve ad gerekli bağlama yapılandırması ile yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="71749-103">Before using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="71749-104">Gerekli öznitelikli türleri COM ile kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="71749-104">To register the required attributed types with COM</span></span>  
  
1.  <span data-ttu-id="71749-105">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta verileri sözleşmeden almak için aracı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="71749-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="71749-106">Bu kaynak kodunu oluşturur bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci derleme ve bir istemci uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="71749-106">This generates the source code for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly and a client application configuration file.</span></span>  
  
2.  <span data-ttu-id="71749-107">Derlemedeki türleri olarak işaretlenmediğinden emin olun `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="71749-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="71749-108">Bunu yapmak için Visual Studio projenizi AssemblyInfo.cs dosyasında şu özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="71749-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  <span data-ttu-id="71749-109">Yönetilen derleme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci tanımlayıcı adlı bir derleme olarak.</span><span class="sxs-lookup"><span data-stu-id="71749-109">Compile the managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as a strong-named assembly.</span></span> <span data-ttu-id="71749-110">Bu, bir şifreleme anahtar çifti ile imzalama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="71749-110">This requires signing with a cryptographic key pair.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="71749-111">[Bir derlemeyi tanımlayıcı adla imzalama](http://go.microsoft.com/fwlink/?LinkId=94874) .NET Geliştirici Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="71749-111"> [Signing an Assembly with a Strong Name](http://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4.  <span data-ttu-id="71749-112">Derleme kaydı (Regasm.exe) aracıyla kullanın `/tlb` türleri com derlemesine kaydetmek için seçeneği</span><span class="sxs-lookup"><span data-stu-id="71749-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5.  <span data-ttu-id="71749-113">Derleme genel derleme önbelleğine eklemek için Genel Derleme Önbelleği (Gacutil.exe) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="71749-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71749-114">Derleme imzalama ve genel derleme önbelleğine ekleme isteğe bağlı adımlardır, ancak çalışma zamanında doğru konumdan derlemesi yüklenirken işlemini kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="71749-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="71749-115">COM uygulama ve ad ile gerekli bağlama yapılandırması yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="71749-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
-   <span data-ttu-id="71749-116">Bağlama tanımları yerleştirin (tarafından oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturulan istemci uygulama yapılandırma dosyasında) istemci uygulamanın yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="71749-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="71749-117">Örneğin, bir Visual Basic CallCenterClient.exe adlı 6.0 için yürütülebilir, yapılandırma, yürütülebilir dosya ile aynı dizinde içinde CallCenterConfig.exe.config adlı bir dosyaya yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="71749-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="71749-118">İstemci uygulaması artık bilinen ad olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71749-118">The client application can now use the moniker.</span></span> <span data-ttu-id="71749-119">Bağlama yapılandırması tarafından sağlanan türleri bağlama standart birini kullanarak gerekli değilse Not [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71749-119">Note that the binding configuration is not required if using one of the standard binding types provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
     <span data-ttu-id="71749-120">Aşağıdaki türü kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="71749-120">The following type is registered.</span></span>  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="71749-121">Uygulama kullanılarak kullanıma sunulan bir `wsHttpBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="71749-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="71749-122">Belirtilen tür ve uygulama yapılandırması için aşağıdaki örnek ad dizeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71749-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="71749-123">Bir başvuru içeren derlemenin ekledikten sonra ek olarak, Visual Basic 6.0 uygulama içinde bu ad dizelerden herhangi biri kullanabilirsiniz `IMathService` türleri, aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="71749-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="71749-124">Bu örnekte, bağlama yapılandırması tanımı `Binding1` vb6appname.exe.config gibi istemci uygulaması için uygun adlandırılmış yapılandırma dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="71749-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71749-125">C#, C++ veya başka bir .NET dil uygulama benzer bir kod kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71749-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="71749-126">: Ad hatalı biçimlendirilmiş olması veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi" hatası döndürür.</span><span class="sxs-lookup"><span data-stu-id="71749-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="71749-127">Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="71749-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="71749-128">Bu konuda VB 6.0 kodundan hizmet bilinen adı kullanma odaklanıyor olsa da, diğer dillerdeki hizmet bilinen adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71749-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="71749-129">C++ içinden bir ad kullanarak kod yazarken oluşturulan Svcutil.exe derleme aşağıdaki kodda gösterildiği gibi "ile no_namespace named_guids raw_interfaces_only" aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="71749-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="71749-130">Böylece tüm yöntemleri döndürür bu alınan Arabirim tanımları değiştiren bir `HResult`.</span><span class="sxs-lookup"><span data-stu-id="71749-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="71749-131">Diğer tüm dönüş değerleri out Parametreleri uygulamasına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="71749-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="71749-132">Genel yöntemler yürütülmesi aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="71749-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="71749-133">Bu yöntem proxy çağırırken özel bir durum nedenini belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="71749-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="71749-134">Bu işlevsellik yalnızca C++ koddan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71749-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71749-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71749-135">See Also</span></span>  
 [<span data-ttu-id="71749-136">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="71749-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
