---
title: Özel Hizmet Ana Bilgisayarı
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 8302c3c829883da954d200526ca641eb4c169f98
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052032"
---
# <a name="custom-service-host"></a><span data-ttu-id="5bf42-102">Özel Hizmet Ana Bilgisayarı</span><span class="sxs-lookup"><span data-stu-id="5bf42-102">Custom Service Host</span></span>
<span data-ttu-id="5bf42-103">Bu örnek, <xref:System.ServiceModel.ServiceHost> bir hizmetin çalışma zamanı davranışını değiştirmek için sınıfının özel bir türevi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="5bf42-104">Bu yaklaşım, çok sayıda hizmeti yaygın bir şekilde yapılandırmaya yönelik yeniden kullanılabilir bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="5bf42-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="5bf42-105">Örnek ayrıca, <xref:System.ServiceModel.Activation.ServiceHostFactory> Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (was) barındırma ortamında özel bir ServiceHost kullanmak için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5bf42-106">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5bf42-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5bf42-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5bf42-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5bf42-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5bf42-109">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5bf42-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="5bf42-110">Senaryo hakkında</span><span class="sxs-lookup"><span data-stu-id="5bf42-110">About the scenario</span></span>
 <span data-ttu-id="5bf42-111">Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5bf42-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="5bf42-112">Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil.exe gibi) kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="5bf42-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service's metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="5bf42-113">Çok sayıda hizmet için meta veri yayımlamanın etkinleştirilmesi, her bir hizmete aynı yapılandırma öğelerinin eklenmesini ve temelde aynı olan büyük miktarda yapılandırma bilgisine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5bf42-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="5bf42-114">Her hizmeti ayrı ayrı yapılandırmaya alternatif olarak, meta veri yayımlamanın bir kez kullanılmasına izin veren zorunlu kodu yazmak ve daha sonra bu kodu birkaç farklı hizmette yeniden kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5bf42-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="5bf42-115">Bu, ' den türetilen yeni bir sınıf oluşturularak <xref:System.ServiceModel.ServiceHost> ve `ApplyConfiguration` meta veri yayımlama davranışını imperatively eklemek için () yöntemi geçersiz kılılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5bf42-116">Bu örnek, netlik açısından güvenli olmayan bir meta veri yayımlama uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="5bf42-117">Bu uç noktalar, anonim olarak kimliği doğrulanmamış tüketiciler tarafından kullanılabilir ve bir hizmetin meta verilerinin genel olarak kapatılarak emin olmak için bu uç noktaların dağıtılmasından önce gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service's metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="5bf42-118">Özel bir ServiceHost uygulama</span><span class="sxs-lookup"><span data-stu-id="5bf42-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="5bf42-119"><xref:System.ServiceModel.ServiceHost>Sınıfı, bir hizmetin çalışma zamanı davranışını değiştirmek için devralanların geçersiz kılabilmesini sağlayan çeşitli yararlı sanal yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="5bf42-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="5bf42-120">Örneğin, `ApplyConfiguration` () yöntemi yapılandırma deposundan hizmet yapılandırma bilgilerini okur ve konağın <xref:System.ServiceModel.Description.ServiceDescription> uygun şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="5bf42-121">Varsayılan uygulama, uygulamanın yapılandırma dosyasından yapılandırmayı okur.</span><span class="sxs-lookup"><span data-stu-id="5bf42-121">The default implementation reads configuration from the application's configuration file.</span></span> <span data-ttu-id="5bf42-122">Özel uygulamalar `ApplyConfiguration` , () öğesini <xref:System.ServiceModel.Description.ServiceDescription> kullanarak kesinlik temelli kodu daha fazla değiştirebilir ya da varsayılan yapılandırma deposunu tamamen değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="5bf42-123">Örneğin, bir hizmetin uç nokta yapılandırmasını uygulamanın yapılandırma dosyası yerine bir veritabanından okumak için.</span><span class="sxs-lookup"><span data-stu-id="5bf42-123">For example, to read a service's endpoint configuration from a database instead of the application's configuration file.</span></span>  
  
 <span data-ttu-id="5bf42-124">Bu örnekte, bu davranış hizmetin yapılandırma dosyasına açıkça eklenmese bile, ServiceMetadataBehavior (meta veri yayımlamayı sağlayan) ekleyen özel bir ServiceHost oluşturmak istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="5bf42-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior (which enables metadata publishing) even if this behavior is not explicitly added in the service's configuration file.</span></span> <span data-ttu-id="5bf42-125">Bunu gerçekleştirmek için, <xref:System.ServiceModel.ServiceHost> ve geçersiz kılmalar () öğesinden devralan yeni bir sınıf oluşturun `ApplyConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5bf42-125">To accomplish this, create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```csharp
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
  
 <span data-ttu-id="5bf42-126">Uygulamanın yapılandırma dosyasında sağlanmış olan herhangi bir yapılandırmayı yoksaymak istemediğimiz için, () geçersiz kıldığımız ilk şey `ApplyConfiguration` temel uygulamayı çağırır.</span><span class="sxs-lookup"><span data-stu-id="5bf42-126">Because we do not want to ignore any configuration that has been provided in the application's configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="5bf42-127">Bu yöntem tamamlandıktan sonra, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> aşağıdaki zorunlu kodu kullanarak açıklamaya imperatively ekleyebiliriz.</span><span class="sxs-lookup"><span data-stu-id="5bf42-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="5bf42-128">`ApplyConfiguration`() Geçersiz kılmanın yapması gereken son şey, varsayılan meta veri uç noktasını eklemektir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="5bf42-129">Kurala göre, hizmet ana bilgisayarının BaseAddresses koleksiyonundaki her bir URI için bir meta veri uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5bf42-129">By convention, one metadata endpoint is created for each URI in the service host's BaseAddresses collection.</span></span>  
  
```csharp
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="5bf42-130">Self ana bilgisayarda özel bir ServiceHost kullanma</span><span class="sxs-lookup"><span data-stu-id="5bf42-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="5bf42-131">Özel ServiceHost uygulamamızı tamamladığımıza göre, bu hizmeti bir örneğinin içinde barındırarak herhangi bir hizmete meta veri yayımlama davranışı eklemek için bunu kullanabiliriz `SelfDescribingServiceHost` .</span><span class="sxs-lookup"><span data-stu-id="5bf42-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="5bf42-132">Aşağıdaki kod, kendi kendine ana bilgisayar senaryosunda nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="5bf42-133">Hizmeti barındırmak için varsayılan sınıfı kullandığımız için özel ana bilgisayar, uygulamanın yapılandırma dosyasından hizmetin uç nokta yapılandırmasını yine de okur <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="5bf42-133">Our custom host still reads the service's endpoint configuration from the application's configuration file, as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="5bf42-134">Ancak, özel ana bilgisayar içinde meta veri yayımlamayı etkinleştirmeye yönelik mantığı eklediğimiz için, artık yapılandırmada meta veri yayımlama davranışını açıkça etkinleştirmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="5bf42-135">Bu yaklaşım, birkaç hizmet içeren bir uygulama oluştururken ve aynı yapılandırma öğelerini ve üzerine yazmadan her birinde meta veri yayımlamayı etkinleştirmek istediğinizde ayrı bir avantaja sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="5bf42-136">IIS 'de veya WAS 'de özel bir ServiceHost kullanma</span><span class="sxs-lookup"><span data-stu-id="5bf42-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="5bf42-137">Hizmet ana bilgisayarı örneğini oluşturup açmaktan sorumlu olan uygulama kodunuz olduğundan, Self-Host senaryolarında özel bir hizmet ana bilgisayarı kullanılması basittir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="5bf42-138">Ancak, IIS veya barındırma ortamında, WCF altyapısı gelen iletilere yanıt olarak hizmetinizin ana bilgisayarını dinamik olarak örnekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service's host in response to incoming messages.</span></span> <span data-ttu-id="5bf42-139">Özel hizmet ana bilgisayarları da bu barındırma ortamında kullanılabilir, ancak bir ServiceHostFactory biçiminde bazı ek kodlar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="5bf42-140">Aşağıdaki kod, <xref:System.ServiceModel.Activation.ServiceHostFactory> özel örneklerimizi döndüren bir türevi gösterir `SelfDescribingServiceHost` .</span><span class="sxs-lookup"><span data-stu-id="5bf42-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="5bf42-141">Gördüğünüz gibi, özel bir ServiceHostFactory uygulamak basittir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-141">As you can see, implementing a custom ServiceHostFactory is straightforward.</span></span> <span data-ttu-id="5bf42-142">Tüm özel mantık, ServiceHost uygulamasının içinde bulunur; Factory, türetilmiş sınıfın bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5bf42-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="5bf42-143">Hizmet uygulamasıyla özel bir fabrika kullanmak için hizmetin. svc dosyasına bazı ek meta veriler eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-143">To use a custom factory with a service implementation, we must add some additional metadata to the service's .svc file.</span></span>  
  
```aspx-csharp
<% @ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="5bf42-144">Burada, yönergeye ek bir `Factory` öznitelik ekledik `@ServiceHost` ve öznitelik değeri olarak özel fabrikamızın clr türü adını geçirdik.</span><span class="sxs-lookup"><span data-stu-id="5bf42-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute's value.</span></span> <span data-ttu-id="5bf42-145">IIS veya bu hizmet için bir ileti aldığında, WCF barındırma altyapısı ilk olarak bir ServiceHostFactory örneği oluşturur ve ardından çağırarak hizmet ana bilgisayarını başlatır `ServiceHostFactory.CreateServiceHost()` .</span><span class="sxs-lookup"><span data-stu-id="5bf42-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiates the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="5bf42-146">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5bf42-146">Running the sample</span></span>  
 <span data-ttu-id="5bf42-147">Bu örnek tam işlevli bir istemci ve hizmet uygulamasını sağlasa da, örnek noktası, bir hizmetin çalışma zamanı davranışının özel bir ana bilgisayar aracılığıyla nasıl değiştirileceğini gösterir. aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="5bf42-147">Although this sample does provide a fully functional client and service implementation, the point of the sample is to illustrate how to alter a service's run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="5bf42-148">Özel ana bilgisayarın etkisini gözlemleyin</span><span class="sxs-lookup"><span data-stu-id="5bf42-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="5bf42-149">Hizmetin Web.config dosyasını açın ve hizmet için açık bir yapılandırma olmadığını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="5bf42-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="5bf42-150">Hizmetin. svc dosyasını açın ve @ServiceHost yönergesinin, özel bir ServiceHostFactory adını belirten bir Factory özniteliği içerdiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="5bf42-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="5bf42-151">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5bf42-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="5bf42-152">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5bf42-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5bf42-153">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5bf42-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="5bf42-154">Çözüm oluşturulduktan sonra, ServiceModelSamples uygulamasını IIS 7,0 ' de ayarlamak için Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5bf42-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="5bf42-155">ServiceModelSamples dizini artık bir IIS 7,0 uygulaması olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="5bf42-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="5bf42-156">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5bf42-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="5bf42-157">IIS 7,0 uygulamasını kaldırmak için *Cleanup.bat*çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5bf42-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bf42-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bf42-158">See also</span></span>

- [<span data-ttu-id="5bf42-159">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="5bf42-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
