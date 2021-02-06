---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: hizmet bilinen adını kaydetme ve yapılandırma'
title: 'Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: 9c6867941a5b96c6ced0f8e371e10697144bd121
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643468"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="e72ad-103">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e72ad-103">How to: Register and Configure a Service Moniker</span></span>

<span data-ttu-id="e72ad-104">Türü belirlenmiş bir sözleşmeyle bir COM uygulaması içinde Windows Communication Foundation (WCF) hizmet bilinen adını kullanmadan önce, gerekli olan türleri COM 'a kaydetmeniz ve COM uygulamasını ve bilinen adı gerekli bağlama yapılandırması ile yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e72ad-104">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>

## <a name="register-the-required-attributed-types-with-com"></a><span data-ttu-id="e72ad-105">Gerekli öznitelikli türleri COM 'a kaydetme</span><span class="sxs-lookup"><span data-stu-id="e72ad-105">Register the required attributed types with COM</span></span>

1. <span data-ttu-id="e72ad-106">WCF hizmetinden meta veri sözleşmesini almak için [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e72ad-106">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="e72ad-107">Bu, bir WCF istemci derlemesi ve bir istemci uygulama yapılandırma dosyası için kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e72ad-107">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>

2. <span data-ttu-id="e72ad-108">Derlemedeki türlerin olarak işaretlendiğinden emin olun `ComVisible` .</span><span class="sxs-lookup"><span data-stu-id="e72ad-108">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="e72ad-109">Bunu yapmak için, Visual Studio projenizdeki *AssemblyInfo.cs* dosyasına aşağıdaki özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e72ad-109">To do so, add the following attribute to the *AssemblyInfo.cs* file in your Visual Studio project.</span></span>

    ```csharp
    [assembly: ComVisible(true)]
    ```

3. <span data-ttu-id="e72ad-110">Yönetilen WCF istemcisini tanımlayıcı adlı bir derleme olarak derleyin.</span><span class="sxs-lookup"><span data-stu-id="e72ad-110">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="e72ad-111">Bu, bir şifreleme anahtar çiftiyle imza gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e72ad-111">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="e72ad-112">Daha fazla bilgi için bkz. [bir derlemeyi güçlü bir adla imzalama](../../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="e72ad-112">For more information, see [Signing an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>

4. <span data-ttu-id="e72ad-113">Derlemeyi `-tlb` com ile derlemeye kaydetme seçeneğiyle birlikte derleme kaydı (Regasm.exe) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e72ad-113">Use the Assembly Registration (Regasm.exe) tool with the `-tlb` option to register the types in the assembly with COM.</span></span>

5. <span data-ttu-id="e72ad-114">Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için genel bütünleştirilmiş kod önbelleği (Gacutil.exe) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e72ad-114">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e72ad-115">Derlemeyi imzalama ve genel bütünleştirilmiş kod önbelleğine ekleme isteğe bağlı adımlardır, ancak çalışma zamanında derlemeyi doğru konumdan yükleme işlemini basitleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e72ad-115">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>

## <a name="configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="e72ad-116">COM uygulamasını ve bilinen adı gerekli bağlama yapılandırmasıyla yapılandırın</span><span class="sxs-lookup"><span data-stu-id="e72ad-116">Configure the COM application and the moniker with the required binding configuration</span></span>

- <span data-ttu-id="e72ad-117">İstemci uygulamasının yapılandırma dosyasındaki bağlama tanımlarını (oluşturulan istemci uygulama yapılandırma dosyasında bulunan [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan) yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e72ad-117">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="e72ad-118">Örneğin, CallCenterClient.exe adlı bir Visual Basic 6,0 yürütülebilir dosyası için yapılandırma, yürütülebilir dosya ile aynı dizin içinde CallCenterConfig.exe.config adlı bir dosyaya yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e72ad-118">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="e72ad-119">İstemci uygulaması artık bilinen adı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e72ad-119">The client application can now use the moniker.</span></span> <span data-ttu-id="e72ad-120">WCF tarafından sunulan standart bağlama türlerinden birini kullanıyorsanız bağlama yapılandırmasının gerekli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e72ad-120">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>

     <span data-ttu-id="e72ad-121">Aşağıdaki tür kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e72ad-121">The following type is registered.</span></span>

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

     <span data-ttu-id="e72ad-122">Uygulama, bağlama kullanılarak gösterilir `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="e72ad-122">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="e72ad-123">Verilen tür ve uygulama yapılandırması için aşağıdaki örnek bilinen ad dizeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e72ad-123">For the given type and application configuration, the following example moniker strings are used.</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1
    ```

     <span data-ttu-id="e72ad-124">veya</span><span class="sxs-lookup"><span data-stu-id="e72ad-124">or</span></span>

    ```
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}
    ```

     <span data-ttu-id="e72ad-125">Aşağıdaki örnek kodda gösterildiği gibi, türleri içeren derlemeye bir başvuru ekledikten sonra, bir Visual Basic 6,0 uygulaması içinden bu bilinen ad dizelerinin birini kullanabilirsiniz `IMathService` .</span><span class="sxs-lookup"><span data-stu-id="e72ad-125">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>

    ```vb
    Dim mathProxy As IMathService
    Dim result As Integer

    Set mathProxy = GetObject( _
            "service4:address=http://localhost/MathService, _
            binding=wsHttpBinding, _
            bindingConfiguration=Binding1")

    result = mathProxy.Add(3, 5)
    ```

     <span data-ttu-id="e72ad-126">Bu örnekte, bağlama yapılandırması tanımı, `Binding1` istemci uygulaması için *vb6appname.exe.config* gibi bir uygun şekilde adlı yapılandırma dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="e72ad-126">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as *vb6appname.exe.config*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e72ad-127">Benzer kodu C#, C++ veya diğer herhangi bir .NET dil uygulamasında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e72ad-127">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e72ad-128">Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" hatası döndürür.</span><span class="sxs-lookup"><span data-stu-id="e72ad-128">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="e72ad-129">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e72ad-129">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>

     <span data-ttu-id="e72ad-130">Bu konu, Visual Basic 6,0 kodundan hizmet bilinen adını kullanmaya odaklansa da, diğer dillerden bir hizmet bilinen adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e72ad-130">Although this topic focuses on using the service moniker from Visual Basic 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="e72ad-131">C++ kodundan bilinen bir ad kullanırken, Svcutil.exe oluşturulan derleme aşağıdaki kodda gösterildiği gibi "no_namespace named_guids raw_interfaces_only" ile içeri aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e72ad-131">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>

    ```cpp
    #import "ComTestProxy.tlb" no_namespace named_guids
    ```

     <span data-ttu-id="e72ad-132">Bu, içeri aktarılan arabirim tanımlarını tüm yöntemlerin bir döndürmesini sağlayacak şekilde değiştirir `HResult` .</span><span class="sxs-lookup"><span data-stu-id="e72ad-132">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="e72ad-133">Diğer tüm dönüş değerleri Out parametrelerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="e72ad-133">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="e72ad-134">Yöntemlerin genel yürütülmesi aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="e72ad-134">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="e72ad-135">Bu, proxy üzerinde bir yöntemi çağırırken bir özel durumun nedenini belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e72ad-135">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="e72ad-136">Bu işlevsellik yalnızca C++ kodundan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e72ad-136">This functionality is only available from C++ code.</span></span>

## <a name="see-also"></a><span data-ttu-id="e72ad-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e72ad-137">See also</span></span>

- [<span data-ttu-id="e72ad-138">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="e72ad-138">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
