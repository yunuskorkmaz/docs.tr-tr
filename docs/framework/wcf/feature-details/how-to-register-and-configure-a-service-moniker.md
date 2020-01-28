---
title: 'Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: fc0b2d00bcc8e3b14c491446f16297c1036b783b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747094"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="24c24-102">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="24c24-102">How to: Register and Configure a Service Moniker</span></span>

<span data-ttu-id="24c24-103">Türü belirlenmiş bir sözleşmeyle bir COM uygulaması içinde Windows Communication Foundation (WCF) hizmet bilinen adını kullanmadan önce, gerekli öznitelikli türleri COM 'a kaydetmeniz ve COM uygulamasını ve bilinen bağlamayı gerekli bağlamaya göre yapılandırmanız gerekir yapılandırmada.</span><span class="sxs-lookup"><span data-stu-id="24c24-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>

## <a name="register-the-required-attributed-types-with-com"></a><span data-ttu-id="24c24-104">Gerekli öznitelikli türleri COM 'a kaydetme</span><span class="sxs-lookup"><span data-stu-id="24c24-104">Register the required attributed types with COM</span></span>

1. <span data-ttu-id="24c24-105">WCF hizmetinden meta veri sözleşmesini almak için [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="24c24-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="24c24-106">Bu, bir WCF istemci derlemesi ve bir istemci uygulama yapılandırma dosyası için kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24c24-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>

2. <span data-ttu-id="24c24-107">Derlemedeki türlerin `ComVisible`olarak işaretlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="24c24-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="24c24-108">Bunu yapmak için, Visual Studio projenizdeki *AssemblyInfo.cs* dosyasına aşağıdaki özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="24c24-108">To do so, add the following attribute to the *AssemblyInfo.cs* file in your Visual Studio project.</span></span>

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. <span data-ttu-id="24c24-109">Yönetilen WCF istemcisini tanımlayıcı adlı bir derleme olarak derleyin.</span><span class="sxs-lookup"><span data-stu-id="24c24-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="24c24-110">Bu, bir şifreleme anahtar çiftiyle imza gerektirir.</span><span class="sxs-lookup"><span data-stu-id="24c24-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="24c24-111">Daha fazla bilgi için bkz. [bir derlemeyi güçlü bir adla imzalama](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="24c24-111">For more information, see [Signing an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

4. <span data-ttu-id="24c24-112">Derlemeyi COM ile derlemeye kaydetmek için `-tlb` seçeneğiyle bütünleştirilmiş kod kaydı (Regasm. exe) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="24c24-112">Use the Assembly Registration (Regasm.exe) tool with the `-tlb` option to register the types in the assembly with COM.</span></span>

5. <span data-ttu-id="24c24-113">Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için genel bütünleştirilmiş kod önbelleği (Gacutil. exe) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="24c24-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>

    > [!NOTE]
    > <span data-ttu-id="24c24-114">Derlemeyi imzalama ve genel bütünleştirilmiş kod önbelleğine ekleme isteğe bağlı adımlardır, ancak çalışma zamanında derlemeyi doğru konumdan yükleme işlemini basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="24c24-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="24c24-115">COM uygulamasını ve bilinen adı gerekli bağlama yapılandırmasıyla yapılandırın</span><span class="sxs-lookup"><span data-stu-id="24c24-115">Configure the COM application and the moniker with the required binding configuration</span></span>

- <span data-ttu-id="24c24-116">İstemci uygulamasının yapılandırma dosyasındaki bağlama tanımlarını (oluşturulan istemci uygulama yapılandırma dosyasında bulunan [ServiceModel meta veri yardımcı programı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan) yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="24c24-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="24c24-117">Örneğin, CallCenterClient. exe adlı bir Visual Basic 6,0 yürütülebilir dosyası için yapılandırma, yürütülebilir dosya ile aynı dizin içinde CallCenterConfig. exe. config adlı bir dosyaya yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="24c24-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="24c24-118">İstemci uygulaması artık bilinen adı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="24c24-118">The client application can now use the moniker.</span></span> <span data-ttu-id="24c24-119">WCF tarafından sunulan standart bağlama türlerinden birini kullanıyorsanız bağlama yapılandırmasının gerekli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="24c24-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>

     <span data-ttu-id="24c24-120">Aşağıdaki tür kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="24c24-120">The following type is registered.</span></span>

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

     <span data-ttu-id="24c24-121">Uygulama `wsHttpBinding` bağlama kullanılarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="24c24-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="24c24-122">Verilen tür ve uygulama yapılandırması için aşağıdaki örnek bilinen ad dizeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24c24-122">For the given type and application configuration, the following example moniker strings are used.</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     <span data-ttu-id="24c24-123">veya</span><span class="sxs-lookup"><span data-stu-id="24c24-123">or</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     <span data-ttu-id="24c24-124">Aşağıdaki örnek kodda gösterildiği gibi, `IMathService` türlerini içeren derlemeye bir başvuru ekledikten sonra, Visual Basic 6,0 uygulamasının içinden bu bilinen ad dizelerinin birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24c24-124">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     <span data-ttu-id="24c24-125">Bu örnekte, bağlama yapılandırma `Binding1` tanımı, istemci uygulaması için *vb6appname. exe. config*gibi bir uygun şekilde adlı yapılandırma dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="24c24-125">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as *vb6appname.exe.config*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="24c24-126">Benzer bir kodu, C# C++bir, veya başka bir .NET dil uygulamasında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24c24-126">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="24c24-127">Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, `GetObject` çağrısı "geçersiz sözdizimi" hatası döndürür.</span><span class="sxs-lookup"><span data-stu-id="24c24-127">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="24c24-128">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="24c24-128">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>

     <span data-ttu-id="24c24-129">Bu konu, Visual Basic 6,0 kodundan hizmet bilinen adını kullanmaya odaklansa da, diğer dillerden bir hizmet bilinen adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24c24-129">Although this topic focuses on using the service moniker from Visual Basic 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="24c24-130">Koddan bilinen bir ad kullanırken C++ , Svcutil. exe tarafından oluşturulan derleme aşağıdaki kodda gösterildiği gibi "no_namespace named_guids raw_interfaces_only" ile içeri aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="24c24-130">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     <span data-ttu-id="24c24-131">Bu, tüm yöntemlerin bir `HResult`döndürmesi için içeri aktarılan arabirim tanımlarını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="24c24-131">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="24c24-132">Diğer tüm dönüş değerleri Out parametrelerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="24c24-132">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="24c24-133">Yöntemlerin genel yürütülmesi aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="24c24-133">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="24c24-134">Bu, proxy üzerinde bir yöntemi çağırırken bir özel durumun nedenini belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="24c24-134">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="24c24-135">Bu işlevsellik yalnızca C++ koddan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24c24-135">This functionality is only available from C++ code.</span></span>

## <a name="see-also"></a><span data-ttu-id="24c24-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24c24-136">See also</span></span>

- [<span data-ttu-id="24c24-137">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="24c24-137">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
