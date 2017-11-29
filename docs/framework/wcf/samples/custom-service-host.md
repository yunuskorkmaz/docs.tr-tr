---
title: "Özel Hizmet Konağı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7fd853ed67b843888b899d0bd0528b293a7520f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-service-host"></a><span data-ttu-id="21497-102">Özel Hizmet Konağı</span><span class="sxs-lookup"><span data-stu-id="21497-102">Custom Service Host</span></span>
<span data-ttu-id="21497-103">Bu örnek özel bir türevi kullanımı gösterilmiştir <xref:System.ServiceModel.ServiceHost> hizmet çalışma zamanı davranışını değiştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="21497-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="21497-104">Bu yaklaşım, hizmetleri, çok sayıda yaygın bir şekilde yapılandırmak için yeniden kullanılabilir bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="21497-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="21497-105">Örnek de nasıl kullanılacağı ortaya <xref:System.ServiceModel.Activation.ServiceHostFactory> Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırma ortamında özel ServiceHost kullanılacak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21497-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="21497-106">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="21497-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="21497-107">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="21497-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="21497-108">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="21497-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21497-109">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="21497-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="21497-110">Senaryo hakkında</span><span class="sxs-lookup"><span data-stu-id="21497-110">About the Scenario</span></span>  
 <span data-ttu-id="21497-111">Olası hassas hizmeti meta verileri, için varsayılan yapılandırma, yanlışlıkla açığa çıkmasını önlemek amacıyla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri, meta veri yayımlama devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="21497-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="21497-112">Bu davranışı varsayılan olarak güvenlidir, ancak ayrıca bir meta veri kullanamayacağı anlamına gelir (örneğin, Svcutil.exe) aracı hizmetin meta veri yayımlama davranışı açıkça yapılandırmasında etkinleştirilmediği sürece hizmetini çağırmak için gerekli istemci kodu oluşturmak üzere, içe.</span><span class="sxs-lookup"><span data-stu-id="21497-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="21497-113">Meta veri yayımlama için çok sayıda Hizmetleri etkinleştirme çok miktarda temelde aynıdır yapılandırma bilgilerini sonuçları her bireysel hizmet aynı yapılandırma öğeleri ekleme kapsar.</span><span class="sxs-lookup"><span data-stu-id="21497-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="21497-114">Her hizmet için ayrı ayrı yapılandırma alternatif olarak, meta veri yayımlama kez sağlayan kesinlik temelli kodu yazma ve daha sonra bu kodu farklı hizmetler arasında yeniden mümkündür.</span><span class="sxs-lookup"><span data-stu-id="21497-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="21497-115">Öğesinden türetilen yeni bir sınıf oluşturarak elde edilir <xref:System.ServiceModel.ServiceHost> ve geçersiz kılmalar `ApplyConfiguration`() yönteminin imperatively meta veri yayımlama davranışı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="21497-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="21497-116">Daha anlaşılır olması için bu örnek nasıl güvenli meta veri yayımlama uç noktası oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21497-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="21497-117">Bu tür uç noktaları anonim kimlik doğrulamasız tüketicilere potansiyel olarak kullanılabilir ve bakım gibi uç noktaları dağıtmadan önce genel olarak disclosing bir hizmetin meta veri uygun olduğundan emin olmak için izlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="21497-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="21497-118">Özel bir ServiceHost uygulama</span><span class="sxs-lookup"><span data-stu-id="21497-118">Implementing a Custom ServiceHost</span></span>  
 <span data-ttu-id="21497-119"><xref:System.ServiceModel.ServiceHost> Sınıfı Notlar hizmet çalışma zamanı davranışını değiştirmek için geçersiz kılabilirsiniz çeşitli yararlı sanal yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="21497-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="21497-120">Örneğin, `ApplyConfiguration`() yönteminin yapılandırma Mağazası'ndan hizmet yapılandırma bilgilerini okur ve ana bilgisayarın değiştirir <xref:System.ServiceModel.Description.ServiceDescription> uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="21497-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="21497-121">Varsayılan uygulama uygulama yapılandırma dosyasından yapılandırma okur.</span><span class="sxs-lookup"><span data-stu-id="21497-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="21497-122">Özel uyarlama kılabilirsiniz `ApplyConfiguration`(') daha fazla alter <xref:System.ServiceModel.Description.ServiceDescription> kesinlik temelli kod kullanarak veya hatta varsayılan yapılandırma deposu tamamen değiştirin.</span><span class="sxs-lookup"><span data-stu-id="21497-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="21497-123">Örneğin, uygulamanın yapılandırma dosyasına yerine bir veritabanından bir hizmetin uç nokta yapılandırması okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="21497-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="21497-124">Bu örnekte (meta veri yayımlama sağlayan) ServiceMetadataBehavior ekleyen özel bir ServiceHost yapı istiyoruz, bile bu davranış hizmet yapılandırma dosyasında açıkça eklenmedi.</span><span class="sxs-lookup"><span data-stu-id="21497-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="21497-125">Bunu başarmak için biz devraldığı yeni bir sınıf oluşturun <xref:System.ServiceModel.ServiceHost> ve geçersiz kılmalar `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="21497-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```  
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to   
    //alter the ServiceDescription prior to opening  
    //the service host.   
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();       
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="21497-126">Uygulamanın yapılandırma dosyasında, ilk şey bizim geçersiz kılma sağlanan herhangi bir yapılandırma yoksay istiyoruz değil çünkü `ApplyConfiguration`() mu temel uygulamayı çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="21497-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="21497-127">Bu yöntem tamamlandığında imperatively ekleyebiliriz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kesinlik temelli aşağıdaki kodu kullanarak açıklaması için.</span><span class="sxs-lookup"><span data-stu-id="21497-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```  
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,   
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="21497-128">Son bizim `ApplyConfiguration`() geçersiz kılma gerçekleştirmelisiniz varsayılan meta veri uç noktası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="21497-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="21497-129">Kurala göre hizmet ana bilgisayarın BaseAddresses koleksiyondaki her URI için bir meta veri uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="21497-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
```  
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="21497-130">Kendini barındırma özel ServiceHost kullanma</span><span class="sxs-lookup"><span data-stu-id="21497-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="21497-131">Biz bizim Özel ServiceHost uygulama tamamladığınıza göre Biz bu hizmet örneği içinde barındırarak herhangi bir hizmetin meta veri yayımlama davranışı eklemek için kullanabilirsiniz bizim `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="21497-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="21497-132">Aşağıdaki kod kendini barındırma senaryosunda kullanmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="21497-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="21497-133">Yalnızca varsayılan olarak kullansaydık bizim Özel konak hizmetin uç nokta yapılandırması uygulama yapılandırma dosyasından hala okur. <xref:System.ServiceModel.ServiceHost> hizmet barındırmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="21497-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="21497-134">Meta veri yayımlama bizim Özel konağın içinde etkinleştirmek için mantığı eklediğimiz olduğundan, ancak biz artık açıkça meta veri yayımlama davranışı yapılandırmasında etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21497-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="21497-135">Bu yaklaşım, birkaç hizmetleri içeren bir uygulama oluşturma ve bunların her birini meta veri yayımlama aynı yapılandırma öğeleri tekrar tekrar yazmak zorunda kalmadan etkinleştirmek istiyorsanız, farklı bir avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="21497-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="21497-136">IIS veya WAS özel ServiceHost kullanma</span><span class="sxs-lookup"><span data-stu-id="21497-136">Using a Custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="21497-137">Uygulama kodunuz oluşturmak ve hizmet ana bilgisayar örneği açmak için sorumlu olduğu için bir özel hizmet ana bilgisayar kendini barındırma senaryolarında kullanarak, basittir.</span><span class="sxs-lookup"><span data-stu-id="21497-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="21497-138">IIS veya barındırma ortamı, ancak WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı dinamik olarak gelen iletilere yanıt olarak hizmetinizin ana bilgisayar örneği.</span><span class="sxs-lookup"><span data-stu-id="21497-138">In the IIS or WAS hosting environment, however, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="21497-139">Özel hizmet ana de bu barındırma ortamında kullanılabilir, ancak bazı ek kod bir ServiceHostFactory biçiminde gerektirir.</span><span class="sxs-lookup"><span data-stu-id="21497-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="21497-140">Aşağıdaki kod bir türevi gösterir <xref:System.ServiceModel.Activation.ServiceHostFactory> bizim Özel örneklerini döndüren `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="21497-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```  
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,   
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)   
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,     
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="21497-141">Gördüğünüz gibi özel ServiceHostFactory uygulama oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="21497-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="21497-142">Tüm özel mantık ServiceHost uygulama içinde bulunur; Fabrika türetilmiş sınıf örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="21497-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="21497-143">Bir hizmet uygulaması ile özel bir Fabrika kullanmak için biz hizmetin .svc dosyasına bazı ek meta veri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21497-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 <span data-ttu-id="21497-144">Burada ek ekledik `Factory` özniteliğini `@ServiceHost` CLR yönerge ve geçirilen özniteliğinin değeri bizim Özel Fabrika adını yazın.</span><span class="sxs-lookup"><span data-stu-id="21497-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="21497-145">IIS ya da WAS bu hizmet için bir ileti aldığında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı barındırma ilk ServiceHostFactory örneği oluşturur ve ardından çağırarak hizmeti konak örneği `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="21497-145">When IIS or WAS receives a message for this service, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="21497-146">Örnek çalışıyor</span><span class="sxs-lookup"><span data-stu-id="21497-146">Running the Sample</span></span>  
 <span data-ttu-id="21497-147">Bu örnek bir tam olarak işlevsel istemci ve hizmet uygulaması sunmasına karşın, örnek bir hizmetin çalışma zamanı davranışı özel konak. yoluyla değiştirmek için aşağıdaki adımları uygulayın nasıl göstermek üzere noktasıdır:</span><span class="sxs-lookup"><span data-stu-id="21497-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a><span data-ttu-id="21497-148">Özel konak etkisini izlemek için</span><span class="sxs-lookup"><span data-stu-id="21497-148">To observe the effect of the custom host</span></span>  
  
1.  <span data-ttu-id="21497-149">Hizmetin Web.config dosyasını açın ve hizmet için meta verileri açıkça etkinleştirme herhangi bir yapılandırma olup olmadığına bakın.</span><span class="sxs-lookup"><span data-stu-id="21497-149">Open the service’s Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2.  <span data-ttu-id="21497-150">Hizmetin .svc dosyasını açın ve görüntülendiğini kendi @ServiceHost yönergesi özel ServiceHostFactory adını belirten bir Fabrika özniteliği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="21497-150">Open the service’s .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21497-151">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="21497-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="21497-152">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21497-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="21497-153">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21497-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="21497-154">Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırmak [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21497-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="21497-155">ServiceModelSamples dizin şimdi olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="21497-155">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="21497-156">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21497-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="21497-157">Kaldırmak için [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Cleanup.bat Çalıştırma uygulaması.</span><span class="sxs-lookup"><span data-stu-id="21497-157">To remove the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] application, run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21497-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21497-158">See Also</span></span>  
 [<span data-ttu-id="21497-159">Nasıl yapılır: IIS'de WCF Hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="21497-159">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
