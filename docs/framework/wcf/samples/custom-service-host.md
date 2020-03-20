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
# <a name="custom-service-host"></a>Özel Hizmet Ana Bilgisayarı
Bu örnek, bir hizmetin <xref:System.ServiceModel.ServiceHost> çalışma zamanı davranışını değiştirmek için sınıfın özel bir türevinin nasıl kullanılacağını gösterir. Bu yaklaşım, çok sayıda hizmeti ortak bir şekilde yapılandırmak için yeniden kullanılabilir bir alternatif sağlar. Örnek ayrıca, Internet Information <xref:System.ServiceModel.Activation.ServiceHostFactory> Services (IIS) veya Windows Process Activation Service (WAS) barındırma ortamında özel bir ServiceHost kullanmak için sınıfınasıl kullanılacağını da gösterir.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Senaryo hakkında
 Potansiyel olarak hassas hizmet meta verilerinin kasıtsız olarak açıklanmasını önlemek için, Windows Communication Foundation (WCF) hizmetleri için varsayılan yapılandırma meta veri yayımlamayı devre dışı kılabilir. Bu davranış varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracını (Svcutil.exe gibi) kullanamayacağınız anlamına da gelir.  
  
 Çok sayıda hizmet için meta veri yayımlamayı etkinleştirmek, her bir hizmete aynı yapılandırma öğelerinin eklenmesini içerir ve bu da büyük miktarda yapılandırma bilgisinin temelde aynı olmasını sağlar. Her hizmeti ayrı ayrı yapılandırmaya alternatif olarak, meta veri yayımlamayı bir kez etkinleştiren zorunlu kodu yazmak ve ardından bu kodu birkaç farklı hizmet arasında yeniden kullanmak mümkündür. Bu, meta veri yayımlama davranışını zorunlu <xref:System.ServiceModel.ServiceHost> olarak eklemek `ApplyConfiguration`için () yönteminden türeten ve geçersiz kılan yeni bir sınıf oluşturarak gerçekleştirilir.  
  
> [!IMPORTANT]
> Bu örnek, açıklık için güvenli olmayan bir meta veri yayımlama bitiş noktasının nasıl oluşturulabildiğini gösterir. Bu tür uç noktalar anonim kimliği doğrulanmamış tüketiciler için kullanılabilir ve bir hizmetin meta verilerinin herkese açık olarak ifşa edilmesinin uygun olduğundan emin olmak için bu uç noktaları dağıtmadan önce dikkatli olunmalıdır.  
  
## <a name="implementing-a-custom-servicehost"></a>Özel bir ServiceHost uygulama
 Sınıf, <xref:System.ServiceModel.ServiceHost> devralanların bir hizmetin çalışma zamanı davranışını değiştirmek için geçersiz kabilecekleri birkaç yararlı sanal yöntem ortaya çıkarır. Örneğin, `ApplyConfiguration`() yöntemi yapılandırma deposundan hizmet yapılandırma bilgilerini okur ve <xref:System.ServiceModel.Description.ServiceDescription> ana bilgisayardakininkini buna göre değiştirir. Varsayılan uygulama, uygulamanın yapılandırma dosyasından yapılandırmayı okur. Özel uygulamalar () `ApplyConfiguration` <xref:System.ServiceModel.Description.ServiceDescription> kullanarak zorunlu kodu daha fazla değiştirmek ve hatta varsayılan yapılandırma deposutamamen değiştirmek için geçersiz kılınabilir. Örneğin, bir hizmetin bitiş noktası yapılandırmasını uygulamanın yapılandırma dosyası yerine bir veritabanından okumak için.  
  
 Bu örnekte, bu davranış hizmetin yapılandırma dosyasına açıkça eklenmese bile ServiceMetadataBehavior (meta veri yayımlamayı sağlayan) ekleyen özel bir ServiceHost oluşturmak istiyoruz. Bunu başarmak için, devralan <xref:System.ServiceModel.ServiceHost> ve geçersiz kılan `ApplyConfiguration`yeni bir sınıf oluştururuz ().  
  
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
  
 Uygulamanın yapılandırma dosyasında sağlanan herhangi bir yapılandırmayı göz ardı etmek istemediğimizden, `ApplyConfiguration`() geçersiz kılmamızın ilk işi temel uygulamayı çağırmaktır. Bu yöntem tamamlandıktan sonra, zorunlu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> olarak aşağıdaki zorunlu kodu kullanarak açıklamaya ekleyebiliriz.  
  
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
  
 () geçersiz `ApplyConfiguration`kılmanın yapması gereken son şey varsayılan meta veri bitiş noktasını eklemektir. Kuralına göre, hizmet ana bilgisayarının BaseAddresses koleksiyonundaki her URI için bir meta veri bitiş noktası oluşturulur.  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Self-host özel bir ServiceHost kullanma  
 Şimdi bizim özel ServiceHost uygulamasını tamamladık, bizim `SelfDescribingServiceHost`bir örnek içinde bu hizmeti barındırarak herhangi bir hizmet meta veri yayımlama davranışı eklemek için kullanabilirsiniz. Aşağıdaki kod, kendi kendine barındırma senaryosunda nasıl kullanılacağını gösterir.  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Özel ana bilgisayarımız, hizmetin barındırmak için varsayılan <xref:System.ServiceModel.ServiceHost> sınıfını kullanmışız gibi, yine de uygulamanın yapılandırma dosyasından hizmetin bitiş noktası yapılandırmasını okur. Ancak, meta veri yayımlamayı özel ana bilgisayarımız içinde etkinleştirme mantığını eklediğimiz için, artık yapılandırmada meta veri yayımlama davranışını açıkça etkinleştirmemiz gerekir. Bu yaklaşım, birden çok hizmet içeren bir uygulama oluşturuyorsanız ve her biri üzerinde aynı yapılandırma öğelerini tekrar tekrar yazmadan meta veri yayımlamayı etkinleştirmek istediğinizde belirgin bir avantaja sahiptir.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>IIS veya WAS'da özel bir ServiceHost kullanma  
 Hizmet ana bilgisayar örneğini oluşturmak ve açmaktan sonuçta sorumlu olan uygulama kodunuz olduğundan, kendi kendine barındırış senaryolarında özel bir hizmet ana bilgisayarı kullanmak kolaydır. Ancak IIS veya WAS barındırma ortamında, WCF altyapısı gelen iletilere yanıt olarak hizmetinizin ana bilgisayarını dinamik olarak anında bir şekilde anında hale getirmektedir. Özel hizmet ana bilgisayarları da bu barındırma ortamında kullanılabilir, ancak serviceHostFactory şeklinde bazı ek kod gerektirir. Aşağıdaki kod, özel <xref:System.ServiceModel.Activation.ServiceHostFactory> `SelfDescribingServiceHost`örnekleri döndüren bir türevi gösterir.  
  
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
  
 Gördüğünüz gibi, özel bir ServiceHostFactory uygulanması çok basittir. Tüm özel mantık ServiceHost uygulamasının içinde bulunur; fabrika türetilmiş sınıfın bir örneğini döndürür.  
  
 Hizmet uygulaması olan özel bir fabrikayı kullanmak için, hizmetin .svc dosyasına bazı ek meta veriler eklememiz gerekir.  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 Burada `@ServiceHost` yönergeye `Factory` ek bir öznitelik ekledik ve özel fabrikamızın CLR türü adını özniteliğin değeri olarak geçtik. IIS veya WAS bu hizmet için bir ileti aldığında, WCF barındırma altyapısı önce ServiceHostFactory'nin bir örneğini `ServiceHostFactory.CreateServiceHost()`oluşturur ve ardından servis ev sahibini arayarak anında  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Bu örnek tam işlevli bir istemci ve hizmet uygulaması sağlasa da, örneklemin amacı, bir hizmetin çalışma zamanı davranışını özel bir ana bilgisayar aracılığı ile nasıl değiştirilemeyeceğini göstermektir., aşağıdaki adımları yapın:  
  
### <a name="observe-the-effect-of-the-custom-host"></a>Özel ana bilgisayar etkisini gözlemleyin
  
1. Hizmetin Web.config dosyasını açın ve hizmet için meta verileri açıkça etkinleştiren bir yapılandırma olmadığını gözlemleyin.  
  
2. Hizmetin .svc dosyasını açın ve @ServiceHost yönergesinin özel bir ServiceHostFactory'nin adını belirten bir Fabrika özniteliği içerdiğini gözlemleyin.  
  
### <a name="set-up-build-and-run-the-sample"></a>Örneği ayarlama, oluşturma ve çalıştırma
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](building-the-samples.md)yönergeleri izleyin.

3. Çözüm yapıldıktan sonra, IIS 7.0'da ServiceModelSamples Uygulamasını ayarlamak için Setup.bat'ı çalıştırın. ServiceModelSamples dizini artık bir IIS 7.0 Uygulaması olarak görünmelidir.

4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](running-the-samples.md)yönergeleri izleyin.

5. IIS 7.0 uygulamasını kaldırmak için *Cleanup.bat'ı*çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](../feature-details/how-to-host-a-wcf-service-in-iis.md)
