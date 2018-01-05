---
title: "Standart uç noktaları kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ac8a9c639099e952f6030f5625958dd2bf84757
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="usage-of-standard-endpoints"></a>Standart uç noktaları kullanma
Bu örnek, hizmet yapılandırma dosyalarını standart uç noktaları kullanımı gösterilmiştir. Standart bir uç noktası için ilişkili ek özellikleri ile bir adresi, bağlama ve sözleşme birleşimi açıklamak için tek bir özellik kullanarak uç nokta tanımları basitleştirme olanak tanır. Bu örnek nasıl tanımlamak ve özel bir standart uç noktası uygulanacağını ve uç belirli özelliklerini tanımlamak nasıl gösterilir.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Hizmet uç noktaları üç parametresi sağlanarak belirtilebilir: Sözleşme ve adresi, bağlama. Sağlanabilir diğer parametreleri davranışı yapılandırmasını, üstbilgiler, dinleme URI vb. içerir. Bazı durumlarda, tüm veya tüm adresleri, bağlamalar ve sözleşmeler değiştiremezsiniz değerlere sahiptir. Bu nedenle, standart uç noktaları kullanmak da mümkündür. Bu tür uç noktaları bazı örnekleri meta verileri exchange uç noktaları ve bulma uç noktaları içerir. Ayrıca standart uç noktaları varsayılan makul bir kümesini sağlayarak kullanılabilirliğini artıran örneğin kendi standart uç noktaları oluşturmak için veya bir sabit doğası bilgi sağlamak zorunda kalmadan hizmet uç noktaları yapılandırılmasını sağlayarak kullanılabilirliğini artıran değerler ve böylece yapılandırma dosyalarını ayrıntı düzeyini azaltır.  
  
 Bu örnek iki projeden oluşan: iki standart uç noktaları tanımlar hizmeti ve istemcinin hizmetiyle iletişim kurar. Standart uç noktaları hizmet yapılandırma dosyasında tanımlanmış Göster aşağıdaki örnekte bir yoludur.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <endpointExtensions>  
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">  
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />  
        <endpoint kind="mexEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <standardEndpoints>  
      <customEndpoint>  
        <standardEndpoint property="True" />  
      </customEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
</configuration>  
```  
  
 Hizmet türü için tanımlanan ilk uç noktası `customEndpoint`, tanımları içinde görülme `<standardEndpoints>` bölümünde, hangi özelliği `property` değeri verildiğinde `true`. Bu ada sahip yeni bir özellik özelleştirilmiş bir uç nokta durumdur. İkinci uç nokta adresi, bağlama ve sözleşme değerlerini sabit bir meta veri uç noktasına karşılık gelir.  
  
 Öğesinden türeyen bir sınıf bir standart bitiş noktası öğesinin tanımlamak için `StandardEndpointElement` oluşturulması gerekir. Bu örnek, söz konusu olduğunda `CustomEndpointElement` aşağıdaki örnekte gösterildiği gibi sınıfı tanımlandı.  
  
```csharp  
public class CustomEndpointElement : StandardEndpointElement  
{  
    public bool Property  
    {  
        get { return (bool)base["property"]; }  
        set { base["property"] = value; }  
    }  
  
    protected override ConfigurationPropertyCollection Properties  
    {  
        get  
        {  
            ConfigurationPropertyCollection properties = base.Properties;  
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));  
            return properties;  
        }  
    }  
  
    protected override Type EndpointType  
    {  
        get { return typeof(CustomEndpoint); }  
    }  
  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)  
    {  
        return new CustomEndpoint();  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;  
        customEndpoint.Property = this.Property;  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;  
        customEndpoint.Property = this.Property;  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
}  
```  
  
 İçinde `CreateServiceEndpoint` işlevi, bir `CustomEndpoint` nesnesi oluşturulur. Tanımına aşağıdaki örnekte gösterilir.  
  
```  
public class CustomEndpoint : ServiceEndpoint  
    {  
        public CustomEndpoint()  
            : this(string.Empty)  
        {  
        }  
  
        public CustomEndpoint(string address)  
            : this(address, ContractDescription.GetContract(typeof(ICalculator)))  
        {  
        }  
  
        public CustomEndpoint(string address, ContractDescription contract)  
            : base(contract)  
        {  
            this.Binding = new BasicHttpBinding();  
            this.IsSystemEndpoint = false;  
        }  
  
        public bool Property  
        {  
            get;  
            set;  
        }  
    }  
```  
  
 Hizmet ve istemci arasındaki iletişimin gerçekleştirmek için İstemci hizmetine hizmet başvurusu oluşturulur. Örnek yerleşik ve yürütülen hizmeti yürütür ve istemci ile iletişim kurar. Olduğundan her zaman hizmetinde bazı değişiklik hizmet başvurusu güncelleştirilmesi gerektiğini unutmayın.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], StandardEndpoints.sln dosyasını açın.  
  
2.  Başlamak birden çok proje etkinleştirin.  
  
    1.  İçinde **Çözüm Gezgini**, standart uç noktaları çözüme sağ tıklayın ve ardından **özellikleri**.  
  
    2.  İçinde **ortak özellikleri**seçin **başlangıç projesi**ve ardından **birden fazla başlangıç projesi**.  
  
    3.  Hizmet projesi ile listesi başlangıcına Taşı **eylem** kümesine **Başlat**.  
  
    4.  İstemci projesi hizmet projesi sonra da WITH move **eylem** kümesine **Başlat**.  
  
         Bu, istemci projesi sonra hizmet projesi yürütülür belirtir.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!NOTE]
>  Bu adımlar işe yaramazsa, ortamınızın düzgün bir şekilde, aşağıdaki adımları kullanarak ayarlandığını emin olun.  
>   
>  1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Tek bir veya birden çok bilgisayar yapılandırması örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`  
  
## <a name="see-also"></a>Ayrıca Bkz.
