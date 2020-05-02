---
title: Özel Hizmet Ana Bilgisayarı
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 70d527599c310cba694624839f14a313f6000337
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728426"
---
# <a name="custom-service-host"></a>Özel Hizmet Ana Bilgisayarı
Bu örnek, bir hizmetin çalışma zamanı davranışını değiştirmek için <xref:System.ServiceModel.ServiceHost> sınıfının özel bir türevi nasıl kullanacağınızı gösterir. Bu yaklaşım, çok sayıda hizmeti yaygın bir şekilde yapılandırmaya yönelik yeniden kullanılabilir bir alternatif sağlar. Örnek ayrıca, Internet Information Services (IIS) veya <xref:System.ServiceModel.Activation.ServiceHostFactory> Windows Işlem etkinleştirme HIZMETI (was) barındırma ortamında özel bir ServiceHost kullanmak için sınıfını nasıl kullanacağınızı gösterir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (wcf) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Senaryo hakkında
 Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır. Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil. exe gibi) kullanamazsınız.  
  
 Çok sayıda hizmet için meta veri yayımlamanın etkinleştirilmesi, her bir hizmete aynı yapılandırma öğelerinin eklenmesini ve temelde aynı olan büyük miktarda yapılandırma bilgisine neden olur. Her hizmeti ayrı ayrı yapılandırmaya alternatif olarak, meta veri yayımlamanın bir kez kullanılmasına izin veren zorunlu kodu yazmak ve daha sonra bu kodu birkaç farklı hizmette yeniden kullanmak mümkündür. Bu, ' den <xref:System.ServiceModel.ServiceHost> türetilen yeni bir sınıf oluşturularak ve meta veri yayımlama davranışını `ApplyConfiguration`imperatively eklemek için () yöntemi geçersiz kılılarak gerçekleştirilir.  
  
> [!IMPORTANT]
> Bu örnek, netlik açısından güvenli olmayan bir meta veri yayımlama uç noktasının nasıl oluşturulacağını göstermektedir. Bu uç noktalar, anonim olarak kimliği doğrulanmamış tüketiciler tarafından kullanılabilir ve bir hizmetin meta verilerinin genel olarak kapatılarak emin olmak için bu uç noktaların dağıtılmasından önce gerçekleştirilmelidir.  
  
## <a name="implementing-a-custom-servicehost"></a>Özel bir ServiceHost uygulama
 <xref:System.ServiceModel.ServiceHost> Sınıfı, bir hizmetin çalışma zamanı davranışını değiştirmek için devralanların geçersiz kılabilmesini sağlayan çeşitli yararlı sanal yöntemler sunar. Örneğin, `ApplyConfiguration`() yöntemi yapılandırma deposundan hizmet yapılandırma bilgilerini okur ve konağın <xref:System.ServiceModel.Description.ServiceDescription> uygun şekilde değiştirir. Varsayılan uygulama, uygulamanın yapılandırma dosyasından yapılandırmayı okur. Özel uygulamalar, <xref:System.ServiceModel.Description.ServiceDescription> ( `ApplyConfiguration`) öğesini kullanarak kesinlik temelli kodu daha fazla değiştirebilir ya da varsayılan yapılandırma deposunu tamamen değiştirebilir. Örneğin, bir hizmetin uç nokta yapılandırmasını uygulamanın yapılandırma dosyası yerine bir veritabanından okumak için.  
  
 Bu örnekte, bu davranış hizmetin yapılandırma dosyasına açıkça eklenmese bile, ServiceMetadataBehavior (meta veri yayımlamayı sağlayan) ekleyen özel bir ServiceHost oluşturmak istiyoruz. Bunu gerçekleştirmek için, ve geçersiz kılmalar <xref:System.ServiceModel.ServiceHost> `ApplyConfiguration`() öğesinden devralan yeni bir sınıf oluşturun.  
  
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
  
 Uygulamanın yapılandırma dosyasında sağlanmış olan herhangi bir yapılandırmayı yoksaymak istemediğimiz için, `ApplyConfiguration`() geçersiz kıldığımız ilk şey temel uygulamayı çağırır. Bu yöntem tamamlandıktan sonra, aşağıdaki zorunlu kodu kullanarak açıklamaya <xref:System.ServiceModel.Description.ServiceMetadataBehavior> imperatively ekleyebiliriz.  
  
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
  
 `ApplyConfiguration`() Geçersiz kılmanın yapması gereken son şey, varsayılan meta veri uç noktasını eklemektir. Kurala göre, hizmet ana bilgisayarının BaseAddresses koleksiyonundaki her bir URI için bir meta veri uç noktası oluşturulur.  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Self ana bilgisayarda özel bir ServiceHost kullanma  
 Özel ServiceHost uygulamamızı tamamladığımıza göre, bu hizmeti bir örneğinin içinde barındırarak herhangi bir hizmete meta veri yayımlama davranışı eklemek için bunu kullanabiliriz `SelfDescribingServiceHost`. Aşağıdaki kod, kendi kendine ana bilgisayar senaryosunda nasıl kullanılacağını gösterir.  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Hizmeti barındırmak için varsayılan <xref:System.ServiceModel.ServiceHost> sınıfı kullandığımız için özel ana bilgisayar, uygulamanın yapılandırma dosyasından hizmetin uç nokta yapılandırmasını yine de okur. Ancak, özel ana bilgisayar içinde meta veri yayımlamayı etkinleştirmeye yönelik mantığı eklediğimiz için, artık yapılandırmada meta veri yayımlama davranışını açıkça etkinleştirmeleri gerekir. Bu yaklaşım, birkaç hizmet içeren bir uygulama oluştururken ve aynı yapılandırma öğelerini ve üzerine yazmadan her birinde meta veri yayımlamayı etkinleştirmek istediğinizde ayrı bir avantaja sahiptir.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>IIS 'de veya WAS 'de özel bir ServiceHost kullanma  
 Hizmet ana bilgisayarı örneğini oluşturup açmaktan sorumlu olan uygulama kodunuz olduğundan, Self-Host senaryolarında özel bir hizmet ana bilgisayarı kullanılması basittir. Ancak, IIS veya barındırma ortamında, WCF altyapısı gelen iletilere yanıt olarak hizmetinizin ana bilgisayarını dinamik olarak örnekleyebilir. Özel hizmet ana bilgisayarları da bu barındırma ortamında kullanılabilir, ancak bir ServiceHostFactory biçiminde bazı ek kodlar gerektirir. Aşağıdaki kod, özel <xref:System.ServiceModel.Activation.ServiceHostFactory> `SelfDescribingServiceHost`örneklerimizi döndüren bir türevi gösterir.  
  
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
  
 Gördüğünüz gibi, özel bir ServiceHostFactory uygulamak basittir. Tüm özel mantık, ServiceHost uygulamasının içinde bulunur; Factory, türetilmiş sınıfın bir örneğini döndürür.  
  
 Hizmet uygulamasıyla özel bir fabrika kullanmak için hizmetin. svc dosyasına bazı ek meta veriler eklememiz gerekir.  
  
```xml
<% @ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 Burada, `Factory` `@ServiceHost` yönergeye ek bir öznitelik ekledik ve öznitelik değeri olarak özel fabrikamızın clr türü adını geçirdik. IIS veya bu hizmet için bir ileti aldığında, WCF barındırma altyapısı ilk olarak bir ServiceHostFactory örneği oluşturur ve ardından çağırarak `ServiceHostFactory.CreateServiceHost()`hizmet ana bilgisayarını başlatır.  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Bu örnek tam işlevli bir istemci ve hizmet uygulamasını sağlasa da, örnek noktası, bir hizmetin çalışma zamanı davranışının özel bir ana bilgisayar aracılığıyla nasıl değiştirileceğini gösterir. aşağıdaki adımları uygulayın:  
  
### <a name="observe-the-effect-of-the-custom-host"></a>Özel ana bilgisayarın etkisini gözlemleyin
  
1. Hizmetin Web. config dosyasını açın ve hizmet için açık bir yapılandırma olmadığını gözlemleyin.  
  
2. Hizmetin. svc dosyasını açın ve @ServiceHost yönergesinin, özel bir ServiceHostFactory adını belirten bir Factory özniteliği içerdiğini gözlemleyin.  
  
### <a name="set-up-build-and-run-the-sample"></a>Örneği kurma, oluşturma ve çalıştırma
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.

3. Çözüm derlendikten sonra, ServiceModelSamples uygulamasını IIS 7,0 ' de ayarlamak için Setup. bat dosyasını çalıştırın. ServiceModelSamples dizini artık bir IIS 7,0 uygulaması olarak görünmelidir.

4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

5. IIS 7,0 uygulamasını kaldırmak için *Cleanup. bat*dosyasını çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](../feature-details/how-to-host-a-wcf-service-in-iis.md)
