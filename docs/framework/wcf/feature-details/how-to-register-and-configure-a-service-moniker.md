---
title: 'Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: cd3b6bbb47dfd72bf70091c9ca4d6fc5e228d950
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221551"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="d7014-102">Nasıl yapılır: Hizmet Bilinen Adını Kaydetme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7014-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="d7014-103">Yazılı sözleşme ile Windows Communication Foundation (WCF) hizmet bilinen adını COM uygulamasından kullanmadan önce gerekli öznitelik türleri COM ile kaydetme ve COM uygulaması ve ad gerekli bağlama ile yapılandırmanız gerekir yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="d7014-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="d7014-104">Gerekli öznitelik türleri COM ile kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="d7014-104">To register the required attributed types with COM</span></span>  
  
1.  <span data-ttu-id="d7014-105">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta veri sözleşmesi WCF hizmetinden almak için aracı.</span><span class="sxs-lookup"><span data-stu-id="d7014-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="d7014-106">Bir WCF istemcisi derleme ve bir istemci uygulama yapılandırma dosyası için kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7014-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>  
  
2.  <span data-ttu-id="d7014-107">Derlemedeki türleri olarak işaretlendiğinden emin olun `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="d7014-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="d7014-108">Bunu yapmak için Visual Studio projesinde AssemblyInfo.cs dosyası şu özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d7014-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  <span data-ttu-id="d7014-109">Yönetilen WCF istemcisini bir tanımlayıcı adlı bütünleştirilmiş kodu olarak derle.</span><span class="sxs-lookup"><span data-stu-id="d7014-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="d7014-110">Bu şifreleme anahtar çifti ile imzalama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d7014-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="d7014-111">Daha fazla bilgi için [bir derlemeyi tanımlayıcı adla imzalama](https://go.microsoft.com/fwlink/?LinkId=94874) .NET Geliştirici Kılavuzu'nda.</span><span class="sxs-lookup"><span data-stu-id="d7014-111">For more information, see [Signing an Assembly with a Strong Name](https://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4.  <span data-ttu-id="d7014-112">Derleme kaydı (Regasm.exe) aracını `/tlb` seçenek türleri derleme com ile kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="d7014-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5.  <span data-ttu-id="d7014-113">Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için Genel Derleme Önbelleği (Gacutil.exe) aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7014-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7014-114">Derleme imzalama ve Genel Derleme Önbelleği'ne ekleyerek isteğe bağlı adımlardır ancak bunlar derleme zamanında doğru konumda yükleme işlemini kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="d7014-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="d7014-115">COM uygulaması ve ad gerekli bağlama yapılandırması ile yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d7014-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
-   <span data-ttu-id="d7014-116">Bağlama tanımları yerleştirin (tarafından oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturulan istemci uygulama yapılandırma dosyasında) istemci uygulamanın yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="d7014-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="d7014-117">Örneğin, bir Visual Basic CallCenterClient.exe adlı 6.0 için yürütülebilir, yapılandırma, yürütülebilir dosya ile aynı dizine içinde CallCenterConfig.exe.config adındaki bir dosyaya yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d7014-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="d7014-118">İstemci uygulaması artık bir ad kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7014-118">The client application can now use the moniker.</span></span> <span data-ttu-id="d7014-119">Bağlama yapılandırması bağlama WCF tarafından sağlanan türler standardını birini kullanıyorsanız, gerekli olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d7014-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>  
  
     <span data-ttu-id="d7014-120">Şu tür kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d7014-120">The following type is registered.</span></span>  
  
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
  
     <span data-ttu-id="d7014-121">Uygulama kullanılarak açılır bir `wsHttpBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="d7014-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="d7014-122">Aşağıdaki örnek ad dizeleri, belirtilen tür ve uygulama yapılandırması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7014-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="d7014-123">Bu ad dizeleri içeren derlemeyi bir başvuru ekledikten sonra bir Visual Basic 6.0 uygulamadaki kullanabilirsiniz `IMathService` türleri, aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d7014-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="d7014-124">Bu örnekte, bağlama yapılandırması için tanım `Binding1` vb6appname.exe.config gibi istemci uygulaması için uygun şekilde adlandırılmış yapılandırma dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="d7014-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7014-125">C#, C++ veya başka bir .NET dil uygulama benzer kodu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7014-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7014-126">: Bilinen adı yanlış biçimlendirilmiş veya hizmet kullanılamıyor durumunda çağrısı `GetObject` "Söz dizimi geçersiz" hatası döndürür.</span><span class="sxs-lookup"><span data-stu-id="d7014-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="d7014-127">Bu hata iletisini alırsanız kullandığınız ad doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d7014-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="d7014-128">Bu konu hizmet bilinen adı VB 6.0 koddan kullanmaya odaklanmıştır olsa da, diğer dillerdeki hizmet bilinen adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7014-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="d7014-129">C++ içinden bir takma ad'ı kullanarak kod olduğunda oluşturulan Svcutil.exe derleme aşağıdaki kodda gösterildiği gibi "ile no_namespace named_guids raw_interfaces_only" aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7014-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="d7014-130">Tüm yöntemler döndürür, bu içeri aktarılan Arabirim tanımları değiştirir bir `HResult`.</span><span class="sxs-lookup"><span data-stu-id="d7014-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="d7014-131">Herhangi bir dönüş değeri, out parametreleri içine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="d7014-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="d7014-132">Genel yöntemler yürütülmesini aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="d7014-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="d7014-133">Bu proxy üzerinde bir yöntemi çağırırken özel durumun nedenini belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7014-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="d7014-134">Bu işlev, yalnızca C++ kodundan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7014-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7014-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7014-135">See Also</span></span>  
 [<span data-ttu-id="d7014-136">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d7014-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
