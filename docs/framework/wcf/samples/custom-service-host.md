---
title: Özel Hizmet Ana Bilgisayarı
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 2aed557d1d045c08aed206660aa7b4b75ffe0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145078"
---
# <a name="custom-service-host"></a><span data-ttu-id="bc8be-102">Özel Hizmet Ana Bilgisayarı</span><span class="sxs-lookup"><span data-stu-id="bc8be-102">Custom Service Host</span></span>
<span data-ttu-id="bc8be-103">Bu örnek, bir hizmetin <xref:System.ServiceModel.ServiceHost> çalışma zamanı davranışını değiştirmek için sınıfın özel bir türevinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="bc8be-104">Bu yaklaşım, çok sayıda hizmeti ortak bir şekilde yapılandırmak için yeniden kullanılabilir bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc8be-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="bc8be-105">Örnek ayrıca, Internet Information <xref:System.ServiceModel.Activation.ServiceHostFactory> Services (IIS) veya Windows Process Activation Service (WAS) barındırma ortamında özel bir ServiceHost kullanmak için sınıfınasıl kullanılacağını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bc8be-106">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bc8be-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bc8be-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bc8be-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="bc8be-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bc8be-109">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc8be-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="bc8be-110">Senaryo hakkında</span><span class="sxs-lookup"><span data-stu-id="bc8be-110">About the scenario</span></span>
 <span data-ttu-id="bc8be-111">Potansiyel olarak hassas hizmet meta verilerinin kasıtsız olarak açıklanmasını önlemek için, Windows Communication Foundation (WCF) hizmetleri için varsayılan yapılandırma meta veri yayımlamayı devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="bc8be-112">Bu davranış varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracını (Svcutil.exe gibi) kullanamayacağınız anlamına da gelir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="bc8be-113">Çok sayıda hizmet için meta veri yayımlamayı etkinleştirmek, her bir hizmete aynı yapılandırma öğelerinin eklenmesini içerir ve bu da büyük miktarda yapılandırma bilgisinin temelde aynı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc8be-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="bc8be-114">Her hizmeti ayrı ayrı yapılandırmaya alternatif olarak, meta veri yayımlamayı bir kez etkinleştiren zorunlu kodu yazmak ve ardından bu kodu birkaç farklı hizmet arasında yeniden kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bc8be-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="bc8be-115">Bu, meta veri yayımlama davranışını zorunlu <xref:System.ServiceModel.ServiceHost> olarak eklemek `ApplyConfiguration`için () yönteminden türeten ve geçersiz kılan yeni bir sınıf oluşturarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bc8be-116">Bu örnek, açıklık için güvenli olmayan bir meta veri yayımlama bitiş noktasının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="bc8be-117">Bu tür uç noktalar anonim kimliği doğrulanmamış tüketiciler için kullanılabilir ve bir hizmetin meta verilerinin herkese açık olarak ifşa edilmesinin uygun olduğundan emin olmak için bu uç noktaları dağıtmadan önce dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc8be-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="bc8be-118">Özel bir ServiceHost uygulama</span><span class="sxs-lookup"><span data-stu-id="bc8be-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="bc8be-119">Sınıf, <xref:System.ServiceModel.ServiceHost> devralanların bir hizmetin çalışma zamanı davranışını değiştirmek için geçersiz kabilecekleri birkaç yararlı sanal yöntem ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="bc8be-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="bc8be-120">Örneğin, `ApplyConfiguration`() yöntemi yapılandırma deposundan hizmet yapılandırma bilgilerini okur ve <xref:System.ServiceModel.Description.ServiceDescription> ana bilgisayardakininkini buna göre değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="bc8be-121">Varsayılan uygulama, uygulamanın yapılandırma dosyasından yapılandırmayı okur.</span><span class="sxs-lookup"><span data-stu-id="bc8be-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="bc8be-122">Özel uygulamalar () `ApplyConfiguration` <xref:System.ServiceModel.Description.ServiceDescription> kullanarak zorunlu kodu daha fazla değiştirmek ve hatta varsayılan yapılandırma deposutamamen değiştirmek için geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="bc8be-123">Örneğin, bir hizmetin bitiş noktası yapılandırmasını uygulamanın yapılandırma dosyası yerine bir veritabanından okumak için.</span><span class="sxs-lookup"><span data-stu-id="bc8be-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="bc8be-124">Bu örnekte, bu davranış hizmetin yapılandırma dosyasına açıkça eklenmese bile ServiceMetadataBehavior (meta veri yayımlamayı sağlayan) ekleyen özel bir ServiceHost oluşturmak istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="bc8be-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="bc8be-125">Bunu başarmak için, devralan <xref:System.ServiceModel.ServiceHost> ve geçersiz kılan `ApplyConfiguration`yeni bir sınıf oluştururuz ().</span><span class="sxs-lookup"><span data-stu-id="bc8be-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
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
  
 <span data-ttu-id="bc8be-126">Uygulamanın yapılandırma dosyasında sağlanan herhangi bir yapılandırmayı göz ardı etmek istemediğimizden, `ApplyConfiguration`() geçersiz kılmamızın ilk işi temel uygulamayı çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="bc8be-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="bc8be-127">Bu yöntem tamamlandıktan sonra, zorunlu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> olarak aşağıdaki zorunlu kodu kullanarak açıklamaya ekleyebiliriz.</span><span class="sxs-lookup"><span data-stu-id="bc8be-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
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
  
 <span data-ttu-id="bc8be-128">() geçersiz `ApplyConfiguration`kılmanın yapması gereken son şey varsayılan meta veri bitiş noktasını eklemektir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="bc8be-129">Kuralına göre, hizmet ana bilgisayarının BaseAddresses koleksiyonundaki her URI için bir meta veri bitiş noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bc8be-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="bc8be-130">Self-host özel bir ServiceHost kullanma</span><span class="sxs-lookup"><span data-stu-id="bc8be-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="bc8be-131">Şimdi bizim özel ServiceHost uygulamasını tamamladık, bizim `SelfDescribingServiceHost`bir örnek içinde bu hizmeti barındırarak herhangi bir hizmet meta veri yayımlama davranışı eklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc8be-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="bc8be-132">Aşağıdaki kod, kendi kendine barındırma senaryosunda nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="bc8be-133">Özel ana bilgisayarımız, hizmetin barındırmak için varsayılan <xref:System.ServiceModel.ServiceHost> sınıfını kullanmışız gibi, yine de uygulamanın yapılandırma dosyasından hizmetin bitiş noktası yapılandırmasını okur.</span><span class="sxs-lookup"><span data-stu-id="bc8be-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="bc8be-134">Ancak, meta veri yayımlamayı özel ana bilgisayarımız içinde etkinleştirme mantığını eklediğimiz için, artık yapılandırmada meta veri yayımlama davranışını açıkça etkinleştirmemiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="bc8be-135">Bu yaklaşım, birden çok hizmet içeren bir uygulama oluşturuyorsanız ve her biri üzerinde aynı yapılandırma öğelerini tekrar tekrar yazmadan meta veri yayımlamayı etkinleştirmek istediğinizde belirgin bir avantaja sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="bc8be-136">IIS veya WAS'da özel bir ServiceHost kullanma</span><span class="sxs-lookup"><span data-stu-id="bc8be-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="bc8be-137">Hizmet ana bilgisayar örneğini oluşturmak ve açmaktan sonuçta sorumlu olan uygulama kodunuz olduğundan, kendi kendine barındırış senaryolarında özel bir hizmet ana bilgisayarı kullanmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="bc8be-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="bc8be-138">Ancak IIS veya WAS barındırma ortamında, WCF altyapısı gelen iletilere yanıt olarak hizmetinizin ana bilgisayarını dinamik olarak anında bir şekilde anında hale getirmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="bc8be-139">Özel hizmet ana bilgisayarları da bu barındırma ortamında kullanılabilir, ancak serviceHostFactory şeklinde bazı ek kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="bc8be-140">Aşağıdaki kod, özel <xref:System.ServiceModel.Activation.ServiceHostFactory> `SelfDescribingServiceHost`örnekleri döndüren bir türevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
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
  
 <span data-ttu-id="bc8be-141">Gördüğünüz gibi, özel bir ServiceHostFactory uygulanması çok basittir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="bc8be-142">Tüm özel mantık ServiceHost uygulamasının içinde bulunur; fabrika türetilmiş sınıfın bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc8be-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="bc8be-143">Hizmet uygulaması olan özel bir fabrikayı kullanmak için, hizmetin .svc dosyasına bazı ek meta veriler eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="bc8be-144">Burada `@ServiceHost` yönergeye `Factory` ek bir öznitelik ekledik ve özel fabrikamızın CLR türü adını özniteliğin değeri olarak geçtik.</span><span class="sxs-lookup"><span data-stu-id="bc8be-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="bc8be-145">IIS veya WAS bu hizmet için bir ileti aldığında, WCF barındırma altyapısı önce ServiceHostFactory'nin bir örneğini `ServiceHostFactory.CreateServiceHost()`oluşturur ve ardından servis ev sahibini arayarak anında</span><span class="sxs-lookup"><span data-stu-id="bc8be-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="bc8be-146">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bc8be-146">Running the sample</span></span>  
 <span data-ttu-id="bc8be-147">Bu örnek tam işlevli bir istemci ve hizmet uygulaması sağlasa da, örneklemin amacı, bir hizmetin çalışma zamanı davranışını özel bir ana bilgisayar aracılığı ile nasıl değiştirilemeyeceğini göstermektir., aşağıdaki adımları yapın:</span><span class="sxs-lookup"><span data-stu-id="bc8be-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="bc8be-148">Özel ana bilgisayar etkisini gözlemleyin</span><span class="sxs-lookup"><span data-stu-id="bc8be-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="bc8be-149">Hizmetin Web.config dosyasını açın ve hizmet için meta verileri açıkça etkinleştiren bir yapılandırma olmadığını gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="bc8be-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="bc8be-150">Hizmetin .svc dosyasını açın ve @ServiceHost yönergesinin özel bir ServiceHostFactory'nin adını belirten bir Fabrika özniteliği içerdiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="bc8be-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="bc8be-151">Örneği ayarlama, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bc8be-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="bc8be-152">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="bc8be-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="bc8be-153">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="bc8be-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="bc8be-154">Çözüm yapıldıktan sonra, IIS 7.0'da ServiceModelSamples Uygulamasını ayarlamak için Setup.bat'ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bc8be-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="bc8be-155">ServiceModelSamples dizini artık bir IIS 7.0 Uygulaması olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="bc8be-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="bc8be-156">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="bc8be-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="bc8be-157">IIS 7.0 uygulamasını kaldırmak için *Cleanup.bat'ı*çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bc8be-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc8be-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc8be-158">See also</span></span>

- [<span data-ttu-id="bc8be-159">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="bc8be-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
