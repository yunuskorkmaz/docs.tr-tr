---
title: 'Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 547e507b4a1115de81532263c34964cd20f15d4e
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972140"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="8e84c-102">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8e84c-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="8e84c-103">Türü belirlenmiş bir sözleşmeyle bir COM uygulaması içinde Windows Communication Foundation (WCF) hizmet bilinen adını kullanmadan önce, gerekli öznitelikli türleri COM 'a kaydetmeniz ve COM uygulamasını ve bilinen bağlamayı gerekli bağlamaya göre yapılandırmanız gerekir yapılandırmada.</span><span class="sxs-lookup"><span data-stu-id="8e84c-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="8e84c-104">Gerekli türleri COM 'a kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="8e84c-104">To register the required attributed types with COM</span></span>  
  
1. <span data-ttu-id="8e84c-105">WCF hizmetinden meta veri sözleşmesini almak için [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e84c-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="8e84c-106">Bu, bir WCF istemci derlemesi ve bir istemci uygulama yapılandırma dosyası için kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8e84c-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>  
  
2. <span data-ttu-id="8e84c-107">Derlemedeki türlerin olarak `ComVisible`işaretlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8e84c-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="8e84c-108">Bunu yapmak için, Visual Studio projenizdeki AssemblyInfo.cs dosyasına aşağıdaki özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8e84c-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```csharp
    [assembly: ComVisible(true)]  
    ```  
  
3. <span data-ttu-id="8e84c-109">Yönetilen WCF istemcisini tanımlayıcı adlı bir derleme olarak derleyin.</span><span class="sxs-lookup"><span data-stu-id="8e84c-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="8e84c-110">Bu, bir şifreleme anahtar çiftiyle imza gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8e84c-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="8e84c-111">Daha fazla bilgi için bkz. .NET geliştirici kılavuzunda [güçlü bir ada sahip bir derlemeyi imzalama](https://go.microsoft.com/fwlink/?LinkId=94874) .</span><span class="sxs-lookup"><span data-stu-id="8e84c-111">For more information, see [Signing an Assembly with a Strong Name](https://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4. <span data-ttu-id="8e84c-112">Derlemeyi com ile derlemeye kaydetme `/tlb` seçeneğiyle birlikte derleme kaydı (Regasm. exe) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e84c-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5. <span data-ttu-id="8e84c-113">Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için genel bütünleştirilmiş kod önbelleği (Gacutil. exe) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e84c-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e84c-114">Derlemeyi imzalama ve genel bütünleştirilmiş kod önbelleğine ekleme isteğe bağlı adımlardır, ancak çalışma zamanında derlemeyi doğru konumdan yükleme işlemini basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8e84c-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="8e84c-115">COM uygulamasını ve bilinen bağlamayı gereken bağlama yapılandırması ile yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="8e84c-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
- <span data-ttu-id="8e84c-116">İstemci uygulamasının yapılandırma dosyasındaki bağlama tanımlarını (oluşturulan istemci uygulama yapılandırma dosyasında bulunan [ServiceModel meta veri yardımcı programı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan) yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="8e84c-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="8e84c-117">Örneğin, CallCenterClient. exe adlı bir Visual Basic 6,0 yürütülebilir dosyası için yapılandırma, yürütülebilir dosya ile aynı dizin içinde CallCenterConfig. exe. config adlı bir dosyaya yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8e84c-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="8e84c-118">İstemci uygulaması artık bilinen adı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8e84c-118">The client application can now use the moniker.</span></span> <span data-ttu-id="8e84c-119">WCF tarafından sunulan standart bağlama türlerinden birini kullanıyorsanız bağlama yapılandırmasının gerekli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8e84c-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>  
  
     <span data-ttu-id="8e84c-120">Aşağıdaki tür kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="8e84c-120">The following type is registered.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="8e84c-121">Uygulama, `wsHttpBinding` bağlama kullanılarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="8e84c-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="8e84c-122">Verilen tür ve uygulama yapılandırması için aşağıdaki örnek bilinen ad dizeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e84c-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ``` 
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ``` 
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="8e84c-123">Aşağıdaki örnek kodda gösterildiği gibi, `IMathService` türleri içeren derlemeye bir başvuru ekledikten sonra, bir Visual Basic 6,0 uygulaması içinden bu bilinen ad dizelerinin birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e84c-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```vb  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="8e84c-124">Bu örnekte, bağlama yapılandırması `Binding1` tanımı, istemci uygulaması için vb6appname. exe. config gibi bir uygun şekilde adlı yapılandırma dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="8e84c-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e84c-125">Benzer bir kodu, C# C++bir, veya başka bir .NET dil uygulamasında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e84c-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e84c-126">: Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" hatası döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e84c-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="8e84c-127">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8e84c-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="8e84c-128">Bu konu, VB 6,0 kodundaki hizmet bilinen adını kullanmaya odaklansa da diğer dillerden bir hizmet bilinen adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e84c-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="8e84c-129">Koddan bilinen bir ad kullanırken C++ , Svcutil. exe tarafından oluşturulan derleme aşağıdaki kodda gösterildiği gibi "no_namespace named_guids raw_interfaces_only" ile içeri aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e84c-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="8e84c-130">Bu, içeri aktarılan arabirim tanımlarını tüm yöntemlerin bir `HResult`döndürmesini sağlayacak şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8e84c-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="8e84c-131">Diğer tüm dönüş değerleri Out parametrelerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8e84c-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="8e84c-132">Yöntemlerin genel yürütülmesi aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="8e84c-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="8e84c-133">Bu, proxy üzerinde bir yöntemi çağırırken bir özel durumun nedenini belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e84c-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="8e84c-134">Bu işlevsellik yalnızca C++ koddan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e84c-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e84c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e84c-135">See also</span></span>

- [<span data-ttu-id="8e84c-136">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="8e84c-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
