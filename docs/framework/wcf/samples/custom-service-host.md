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
# <a name="custom-service-host"></a>Özel Hizmet Konağı
Bu örnek özel bir türevi kullanımı gösterilmiştir <xref:System.ServiceModel.ServiceHost> hizmet çalışma zamanı davranışını değiştirmek için sınıf. Bu yaklaşım, hizmetleri, çok sayıda yaygın bir şekilde yapılandırmak için yeniden kullanılabilir bir alternatif sağlar. Örnek de nasıl kullanılacağı ortaya <xref:System.ServiceModel.Activation.ServiceHostFactory> Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırma ortamında özel ServiceHost kullanılacak sınıfı.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Senaryo hakkında  
 Olası hassas hizmeti meta verileri, için varsayılan yapılandırma, yanlışlıkla açığa çıkmasını önlemek amacıyla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri, meta veri yayımlama devre dışı bırakır. Bu davranışı varsayılan olarak güvenlidir, ancak ayrıca bir meta veri kullanamayacağı anlamına gelir (örneğin, Svcutil.exe) aracı hizmetin meta veri yayımlama davranışı açıkça yapılandırmasında etkinleştirilmediği sürece hizmetini çağırmak için gerekli istemci kodu oluşturmak üzere, içe.  
  
 Meta veri yayımlama için çok sayıda Hizmetleri etkinleştirme çok miktarda temelde aynıdır yapılandırma bilgilerini sonuçları her bireysel hizmet aynı yapılandırma öğeleri ekleme kapsar. Her hizmet için ayrı ayrı yapılandırma alternatif olarak, meta veri yayımlama kez sağlayan kesinlik temelli kodu yazma ve daha sonra bu kodu farklı hizmetler arasında yeniden mümkündür. Öğesinden türetilen yeni bir sınıf oluşturarak elde edilir <xref:System.ServiceModel.ServiceHost> ve geçersiz kılmalar `ApplyConfiguration`() yönteminin imperatively meta veri yayımlama davranışı ekleyin.  
  
> [!IMPORTANT]
>  Daha anlaşılır olması için bu örnek nasıl güvenli meta veri yayımlama uç noktası oluşturulacağını gösterir. Bu tür uç noktaları anonim kimlik doğrulamasız tüketicilere potansiyel olarak kullanılabilir ve bakım gibi uç noktaları dağıtmadan önce genel olarak disclosing bir hizmetin meta veri uygun olduğundan emin olmak için izlenmelidir.  
  
## <a name="implementing-a-custom-servicehost"></a>Özel bir ServiceHost uygulama  
 <xref:System.ServiceModel.ServiceHost> Sınıfı Notlar hizmet çalışma zamanı davranışını değiştirmek için geçersiz kılabilirsiniz çeşitli yararlı sanal yöntemler sunar. Örneğin, `ApplyConfiguration`() yönteminin yapılandırma Mağazası'ndan hizmet yapılandırma bilgilerini okur ve ana bilgisayarın değiştirir <xref:System.ServiceModel.Description.ServiceDescription> uygun şekilde. Varsayılan uygulama uygulama yapılandırma dosyasından yapılandırma okur. Özel uyarlama kılabilirsiniz `ApplyConfiguration`(') daha fazla alter <xref:System.ServiceModel.Description.ServiceDescription> kesinlik temelli kod kullanarak veya hatta varsayılan yapılandırma deposu tamamen değiştirin. Örneğin, uygulamanın yapılandırma dosyasına yerine bir veritabanından bir hizmetin uç nokta yapılandırması okunamıyor.  
  
 Bu örnekte (meta veri yayımlama sağlayan) ServiceMetadataBehavior ekleyen özel bir ServiceHost yapı istiyoruz, bile bu davranış hizmet yapılandırma dosyasında açıkça eklenmedi. Bunu başarmak için biz devraldığı yeni bir sınıf oluşturun <xref:System.ServiceModel.ServiceHost> ve geçersiz kılmalar `ApplyConfiguration`().  
  
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
  
 Uygulamanın yapılandırma dosyasında, ilk şey bizim geçersiz kılma sağlanan herhangi bir yapılandırma yoksay istiyoruz değil çünkü `ApplyConfiguration`() mu temel uygulamayı çağrıdır. Bu yöntem tamamlandığında imperatively ekleyebiliriz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kesinlik temelli aşağıdaki kodu kullanarak açıklaması için.  
  
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
  
 Son bizim `ApplyConfiguration`() geçersiz kılma gerçekleştirmelisiniz varsayılan meta veri uç noktası ekleyin. Kurala göre hizmet ana bilgisayarın BaseAddresses koleksiyondaki her URI için bir meta veri uç noktası oluşturulur.  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Kendini barındırma özel ServiceHost kullanma  
 Biz bizim Özel ServiceHost uygulama tamamladığınıza göre Biz bu hizmet örneği içinde barındırarak herhangi bir hizmetin meta veri yayımlama davranışı eklemek için kullanabilirsiniz bizim `SelfDescribingServiceHost`. Aşağıdaki kod kendini barındırma senaryosunda kullanmak nasıl gösterir.  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Yalnızca varsayılan olarak kullansaydık bizim Özel konak hizmetin uç nokta yapılandırması uygulama yapılandırma dosyasından hala okur. <xref:System.ServiceModel.ServiceHost> hizmet barındırmak için sınıf. Meta veri yayımlama bizim Özel konağın içinde etkinleştirmek için mantığı eklediğimiz olduğundan, ancak biz artık açıkça meta veri yayımlama davranışı yapılandırmasında etkinleştirmeniz gerekir. Bu yaklaşım, birkaç hizmetleri içeren bir uygulama oluşturma ve bunların her birini meta veri yayımlama aynı yapılandırma öğeleri tekrar tekrar yazmak zorunda kalmadan etkinleştirmek istiyorsanız, farklı bir avantajı vardır.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>IIS veya WAS özel ServiceHost kullanma  
 Uygulama kodunuz oluşturmak ve hizmet ana bilgisayar örneği açmak için sorumlu olduğu için bir özel hizmet ana bilgisayar kendini barındırma senaryolarında kullanarak, basittir. IIS veya barındırma ortamı, ancak WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı dinamik olarak gelen iletilere yanıt olarak hizmetinizin ana bilgisayar örneği. Özel hizmet ana de bu barındırma ortamında kullanılabilir, ancak bazı ek kod bir ServiceHostFactory biçiminde gerektirir. Aşağıdaki kod bir türevi gösterir <xref:System.ServiceModel.Activation.ServiceHostFactory> bizim Özel örneklerini döndüren `SelfDescribingServiceHost`.  
  
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
  
 Gördüğünüz gibi özel ServiceHostFactory uygulama oldukça basittir. Tüm özel mantık ServiceHost uygulama içinde bulunur; Fabrika türetilmiş sınıf örneği döndürür.  
  
 Bir hizmet uygulaması ile özel bir Fabrika kullanmak için biz hizmetin .svc dosyasına bazı ek meta veri eklemeniz gerekir.  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 Burada ek ekledik `Factory` özniteliğini `@ServiceHost` CLR yönerge ve geçirilen özniteliğinin değeri bizim Özel Fabrika adını yazın. IIS ya da WAS bu hizmet için bir ileti aldığında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı barındırma ilk ServiceHostFactory örneği oluşturur ve ardından çağırarak hizmeti konak örneği `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Örnek çalışıyor  
 Bu örnek bir tam olarak işlevsel istemci ve hizmet uygulaması sunmasına karşın, örnek bir hizmetin çalışma zamanı davranışı özel konak. yoluyla değiştirmek için aşağıdaki adımları uygulayın nasıl göstermek üzere noktasıdır:  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>Özel konak etkisini izlemek için  
  
1.  Hizmetin Web.config dosyasını açın ve hizmet için meta verileri açıkça etkinleştirme herhangi bir yapılandırma olup olmadığına bakın.  
  
2.  Hizmetin .svc dosyasını açın ve görüntülendiğini kendi @ServiceHost yönergesi özel ServiceHostFactory adını belirten bir Fabrika özniteliği içeriyor.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırmak [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. ServiceModelSamples dizin şimdi olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Kaldırmak için [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Cleanup.bat Çalıştırma uygulaması.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
