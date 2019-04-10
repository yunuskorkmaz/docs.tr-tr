---
title: Özel Hizmet Ana Bilgisayarı
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: d2eebd502fa02d01ac86cf88f336b72829a6116f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340938"
---
# <a name="custom-service-host"></a>Özel Hizmet Ana Bilgisayarı
Bu örnek bir özel türevi nasıl yapılacağı açıklanır <xref:System.ServiceModel.ServiceHost> hizmet çalışma zamanı davranışını değiştirmek için sınıf. Bu yaklaşım, hizmetleri, çok sayıda yaygın bir şekilde yapılandırmak için yeniden kullanılabilir bir alternatif sunar. Örnek ayrıca nasıl kullanılacağını gösterir <xref:System.ServiceModel.Activation.ServiceHostFactory> özel bir ServiceHost Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırma ortamında kullanmak için sınıf.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Bu senaryo hakkında  
 Olası hassas hizmet meta verilerinin yanlışlıkla açığa çıkmasını önlemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma meta veri yayımlamayı devre dışı bırakır. Bu varsayılan olarak güvenli, davranıştır ancak ayrıca Aracı (Svcutil.exe gibi) yapılandırmasında hizmetin meta veri yayımlama davranışı açıkça etkinleştirilmediği hizmeti çağırmak için gereken istemci kodu oluşturmak için içeri bir meta veri kullanamayacağı anlamına gelir.  
  
 Çok sayıda hizmet için meta veri yayımlamayı etkinleştirme, çok miktarda yapılandırma bilgileri, temelde aynıdır sonuçları tek tek her hizmet için aynı yapılandırma öğeleri eklenmesini kapsar. Her hizmet ayrı ayrı yapılandırmaya alternatif olarak, meta veri yayımlama kez sağlayan kesinlik temelli kod yazma ve o kod arasında birkaç farklı hizmetten daha sonra yeniden mümkündür. Bu, türetilen yeni bir sınıf oluşturularak gerçekleştirilir <xref:System.ServiceModel.ServiceHost> ve geçersiz kılmaları `ApplyConfiguration`() yönteminin kesin meta veri yayımlama davranışı eklemek için.  
  
> [!IMPORTANT]
>  Daha anlaşılır olması için bu örnek bir güvenli olmayan meta veri yayımlama uç noktası oluşturma işlemini gösterir. Bu uç noktaları için anonim kimlik doğrulamasız tüketiciler potansiyel olarak kullanılabilir ve bu uç noktaları dağıtmadan önce herkese açık şekilde öğrendiği bir hizmet meta verileri uygun olmasına özen gerekir.  
  
## <a name="implementing-a-custom-servicehost"></a>Özel bir ServiceHost uygulama  
 <xref:System.ServiceModel.ServiceHost> Sınıfı devralanlar hizmet çalışma zamanı davranışını değiştirmek için geçersiz kılabilirsiniz birkaç faydalı sanal yöntemleri gösterir. Örneğin, `ApplyConfiguration`() yönteminin yapılandırma Mağaza'dan hizmet yapılandırma bilgilerini okur ve ana bilgisayarın değiştirir <xref:System.ServiceModel.Description.ServiceDescription> uygun şekilde. Varsayılan uygulama yapılandırma uygulama yapılandırma dosyasından okur. Özel uygulamalar geçersiz kılma `ApplyConfiguration`daha fazla değişiklik yapmak için () <xref:System.ServiceModel.Description.ServiceDescription> kesin kod kullanarak veya hatta varsayılan yapılandırma deposu tamamen değiştirin. Örneğin, uygulamanın yapılandırma dosyası yerine bir veritabanından bir hizmetin uç nokta yapılandırması okunamıyor.  
  
 Bu örnekte (meta veri yayımlama sağlayan) ServiceMetadataBehavior ekleyen özel bir ServiceHost oluşturmak istiyoruz, hizmet yapılandırma dosyasında bile bu davranışı açıkça eklenmez. Öğesinden devralınan yeni bir sınıf oluştururuz Bunu başarmak için <xref:System.ServiceModel.ServiceHost> ve geçersiz kılmaları `ApplyConfiguration`().  
  
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
  
 Uygulamanın yapılandırma dosyasında, ilk şey, bizim geçersiz kılma sağlanmış olan herhangi bir yapılandırma yok saymak değil istediğimizden `ApplyConfiguration`mu () taban uygulamasını çağrıdır. Bu yöntem tamamlandığında, kesin ekleyebiliriz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> aşağıdaki kesin kod kullanarak bir açıklama için.  
  
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
  
 Son bizim `ApplyConfiguration`yapması gerekir () geçersiz kılma varsayılan meta veri uç noktası ekleyin. Kural gereği, hizmet ana bilgisayarın BaseAddresses koleksiyondaki her URI'si için bir meta veri uç noktası oluşturulur.  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Kendi kendini barındıran özel bir ServiceHost kullanma  
 Size özel ServiceHost kararlılığımızın tamamladığımıza göre bu hizmetin bir örneğini içinde barındırarak herhangi bir hizmeti meta veri yayımlama davranışı eklemek için kullanabiliriz bizim `SelfDescribingServiceHost`. Aşağıdaki kod, barındırma senaryosunda kullanma işlemini gösterir.  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Sadece biz varsayılan senaryosuyla bizim Özel ana bilgisayar hizmet uç noktası yapılandırmasını yine de uygulama yapılandırma dosyasından okur. <xref:System.ServiceModel.ServiceHost> Hizmeti'ni barındıracak şekilde sınıfı. Meta veri yayımlama bizim içinde özel bir ana bilgisayar etkinleştir mantığının ekledik olduğundan, ancak biz artık açıkça yapılandırmasında yayımlama davranışı meta verileri etkinleştirmeniz gerekir. Bu yaklaşım, çeşitli hizmetleri içeren bir uygulama oluşturuyorsanız ve tekrar tekrar aynı yapılandırma öğeleri yazmadan her biri meta veri yayımlamayı etkinleştirmek istediğiniz zaman bir ayrı avantajına sahiptir.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>IIS veya WAS özel bir ServiceHost kullanma  
 Uygulama kodunuza oluşturma ve hizmet ana örneği açma sonuçta sorumlu olduğu için bir özel hizmet konağı barındırma senaryolarında kullanımı, açıktır. Ancak, IIS ya da barındırma ortamı WAS'ta WCF altyapısı dinamik olarak hizmetinizin gelen iletiye yanıt olarak ana bilgisayar örnekleme. Özel hizmet konakları bu barındırma ortamı içinde de kullanılabilir, ancak bazı ek kod bir ServiceHostFactory biçiminde gerektirir. Aşağıdaki kod bir türevi gösterir <xref:System.ServiceModel.Activation.ServiceHostFactory> bizim Özel örneklerini döndüren `SelfDescribingServiceHost`.  
  
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
  
 Gördüğünüz gibi bir özel ServiceHostFactory uygulama çok basittir. Tüm özel mantığı ServiceHost uygulama içinde bulunur; Fabrika türetilmiş bir sınıf örneğini döndürür.  
  
 Bir hizmet uygulaması ile özel bir Fabrika kullanmak için size hizmetin .svc dosyasına bazı ek meta veriler eklemeniz gerekir.  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 Burada ek ekledik `Factory` özniteliğini `@ServiceHost` CLR yönerge ve geçirilen özniteliğin değeri özel fabrikadan adını yazın. Bu hizmet için bir ileti aldığında, IIS veya WAS WCF barındırma altyapısını ilk ServiceHostFactory örneği oluşturur ve ardından çağırarak hizmeti konak örneği `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Bu örnek, bir tam işlevsel istemci ve hizmet uygulaması sağlamasına rağmen aşağıdaki adımları uygulayın, bir hizmetin çalışma zamanı davranışını bir özel konak yoluyla alter nasıl göstermek için örnek noktası verilmiştir:  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>Özel ana bilgisayarı etkisini gözlemlemek için  
  
1. Hizmetin Web.config dosyasını açın ve hizmet için meta verileri açıkça etkinleştirme herhangi bir yapılandırma olup olmadığına bakın.  
  
2. Hizmetin .svc dosyasını açın ve mesajının görüntülendiğini görün, @ServiceHost yönergesi özel ServiceHostFactory adını belirten bir Fabrika özniteliği içeriyor.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırma [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. ServiceModelSamples dizin artık olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.  
  
4. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Kaldırılacak [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Cleanup.bat Çalıştırma uygulaması.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
