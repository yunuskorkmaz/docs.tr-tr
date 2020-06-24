---
title: Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
description: WCF uygulamalarında davranış arabirimlerini uygulamayı ve program aracılığıyla veya bir yapılandırma dosyasında bir hizmet açıklamasına ya da uç noktaya eklemeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: fc297f593b744d69cb09a33be6816fb646f88b67
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247591"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
Davranışlar, varsayılan davranışı değiştirmenize ve Windows Communication Foundation (WCF) istemci ve hizmet uygulamalarında hizmet yapılandırmasını incelemek ve doğrulamak veya çalışma zamanı davranışını değiştirmek için özel uzantılar eklemenize olanak tanır. Bu konu, davranış arabirimlerini, bunların nasıl uygulanacağını ve hizmet açıklamasına (bir hizmet uygulamasına) veya uç noktaya (bir istemci uygulamasında) program aracılığıyla veya bir yapılandırma dosyasına nasıl ekleneceğini açıklar. Sistem tarafından sunulan davranışları kullanma hakkında daha fazla bilgi için bkz. [hizmet çalışma zamanı davranışını belirtme](../specifying-service-run-time-behavior.md) ve [Istemci çalışma zamanı davranışını belirtme](../specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Davranışlar  
 Davranış türleri, hizmet veya hizmet uç noktası açıklaması nesnelerine (sırasıyla hizmet veya istemci), bu nesneler bir WCF hizmetini veya WCF istemcisini yürüten bir çalışma zamanı oluşturmak için Windows Communication Foundation (WCF) tarafından kullanılmadan önce eklenir. Çalışma zamanı oluşturma işlemi sırasında bu davranışlar çağrıldığında, çalışma zamanı özelliklerine ve anlaşma, bağlamalar ve adresler tarafından oluşturulan çalışma zamanını değiştiren yöntemlere erişebilecektir.  
  
### <a name="behavior-methods"></a>Davranış yöntemleri  
 Tüm davranışlar bir `AddBindingParameters` yönteme, `ApplyDispatchBehavior` yönteme, `Validate` yönteme ve `ApplyClientBehavior` bir özel durum içeren bir yönteme sahiptir: <xref:System.ServiceModel.Description.IServiceBehavior> bir istemcide yürütülemediğinden, uygulamaz `ApplyClientBehavior` .  
  
- Özel `AddBindingParameters` bağlamaların çalışma zamanı oluşturulduğunda kullanımları için erişebileceği bir koleksiyona özel nesneler eklemek veya değiştirmek için yöntemini kullanın. Örneğin, bu, kanalın oluşturulduğu, ancak kanal geliştiricisi tarafından bilinmediği, koruma gereksinimlerinin nasıl belirtileceğine ilişkin bir yöntemdir.  
  
- `Validate`Bir dizi ölçüte uyduğundan emin olmak için açıklama ağacını ve ilgili çalışma zamanı nesnesini incelemek üzere yöntemini kullanın.  
  
- `ApplyDispatchBehavior`Ve yöntemleri, `ApplyClientBehavior` Açıklama ağacını incelemek ve hizmet ya da istemcide belirli bir kapsamın çalışma zamanını değiştirmek için kullanın. Ayrıca uzantı nesneleri de ekleyebilirsiniz.  
  
    > [!NOTE]
    > Bu yöntemlerde bir açıklama ağacı sağlanmış olsa da, yalnızca İnceleme amaçlıdır. Bir açıklama ağacı değiştirilirse, davranış tanımsızdır.  
  
 Değiştirebileceğiniz özelliklere ve uygulayabileceğiniz özelleştirme arabirimlerine hizmet ve istemci çalışma zamanı sınıfları üzerinden erişilir. Hizmet türleri <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıflarıdır. İstemci türleri <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.ClientOperation> sınıflarıdır. <xref:System.ServiceModel.Dispatcher.ClientRuntime>Ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfları, sırasıyla istemci genelindeki ve hizmet genelindeki çalışma zamanı özelliklerine ve uzantı koleksiyonlarına erişmek için genişletilebilirlik giriş noktalarıdır. Benzer şekilde, <xref:System.ServiceModel.Dispatcher.ClientOperation> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları sırasıyla istemci işlemini ve hizmet işlemi çalışma zamanı özelliklerini ve uzantı koleksiyonlarını da kullanıma sunar. Ancak, daha geniş kapsamlı çalışma zamanı nesnesine işlem çalışma zamanı nesnesinden erişebilir ve gerekirse bunun tersini yapabilirsiniz.  
  
> [!NOTE]
> Bir istemcinin yürütme davranışını değiştirmek için kullanabileceğiniz çalışma zamanı özellikleri ve uzantı türleri hakkında bir tartışma için bkz. [Istemcileri genişletme](extending-clients.md). Bir hizmet dağıtıcısı 'nin yürütme davranışını değiştirmek için kullanabileceğiniz çalışma zamanı özellikleri ve uzantı türleri hakkında bir tartışma için bkz. [dispatchers 'ı genişletme](extending-dispatchers.md).  
  
 Çoğu WCF kullanıcısı çalışma zamanında doğrudan etkileşime girmez; Bunun yerine, yapılandırma dosyalarındaki sınıflarda veya davranışlarda uç noktalar, sözleşmeler, bağlamalar, adresler ve davranış öznitelikleri gibi temel programlama modeli yapılarını kullanırlar. Bu yapılar, açıklama ağacı tarafından tanımlanan bir hizmet veya istemciyi desteklemek için bir çalışma zamanı oluşturma belirtiminin tamamı olan *Açıklama ağacını*oluşturur.  
  
 WCF 'de dört tür davranış vardır:  
  
- Hizmet davranışları ( <xref:System.ServiceModel.Description.IServiceBehavior> türler), dahil olmak üzere tüm hizmet çalışma zamanının özelleştirilmesini etkinleştirir <xref:System.ServiceModel.ServiceHostBase> .  
  
- Uç nokta davranışları ( <xref:System.ServiceModel.Description.IEndpointBehavior> türler) hizmet uç noktalarının ve bunlarla ilişkili nesnelerin özelleştirilmesini etkinleştirir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> .  
  
- Anlaşma davranışları ( <xref:System.ServiceModel.Description.IContractBehavior> türler) <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> , sırasıyla istemci ve hizmet uygulamalarında hem hem de sınıflarının özelleştirilmesini etkinleştirir.  
  
- İşlem davranışları ( <xref:System.ServiceModel.Description.IOperationBehavior> türler), ve sınıflarının özelleştirmesini, <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> istemci ve hizmette yeniden etkinleştirir.  
  
 Bu davranışları çeşitli açıklama nesnelerine, uygulama yapılandırma dosyalarını kullanarak veya doğrudan ilgili açıklama nesnesindeki davranışlar koleksiyonuna ekleyerek ekleyebilirsiniz. Ancak, veya ' a çağrılmadan önce bir hizmet açıklamasına veya hizmet uç noktası açıklama nesnesine eklenmelidir <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ChannelFactory%601> .  
  
### <a name="behavior-scopes"></a>Davranış kapsamları  
 Her biri çalışma zamanı erişiminin belirli bir kapsamına karşılık gelen dört davranış türü vardır.  
  
#### <a name="service-behaviors"></a>Hizmet davranışları  
 Hizmetini uygulayan hizmet davranışları, <xref:System.ServiceModel.Description.IServiceBehavior> hizmet çalışma zamanının tamamını değiştirdiğiniz birincil mekanizmadır. Hizmete hizmet davranışları eklemek için üç mekanizma vardır.  
  
1. Hizmet sınıfında bir özniteliği kullanılıyor.  Bir oluşturulduğunda <xref:System.ServiceModel.ServiceHost> , <xref:System.ServiceModel.ServiceHost> uygulama, hizmet türündeki öznitelik kümesini saptamak için yansıma kullanır. Bu özniteliklerden herhangi biri uygulamalarsa <xref:System.ServiceModel.Description.IServiceBehavior> , üzerindeki davranışlar koleksiyonuna eklenir <xref:System.ServiceModel.Description.ServiceDescription> . Bu, bu davranışların hizmet çalışma zamanının oluşturulmasına katılmasına izin verir.  
  
2. Davranışı ' de davranış koleksiyonuna programlı bir şekilde ekleme <xref:System.ServiceModel.Description.ServiceDescription> . Bu, aşağıdaki kod satırlarıyla gerçekleştirilebilir:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Yapılandırmayı genişleten özel bir uygulama <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> . Bu, uygulama yapılandırma dosyalarından hizmet davranışının kullanılmasına izin vermez.  
  
 WCF 'de hizmet davranışlarına örnek <xref:System.ServiceModel.ServiceBehaviorAttribute> olarak öznitelik,, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı dahildir.  
  
#### <a name="contract-behaviors"></a>Sözleşme davranışları  
 Arabirimini uygulayan sözleşme davranışları, <xref:System.ServiceModel.Description.IContractBehavior> hem istemci hem de hizmet çalışma zamanını bir sözleşme genelinde genişletmek için kullanılır.  
  
 Sözleşmeye sözleşme davranışları eklemek için iki mekanizma vardır.  İlk mekanizma, sözleşme arabiriminde kullanılacak özel bir öznitelik oluşturmaktır. Bir sözleşme arabirimi bir <xref:System.ServiceModel.ServiceHost> veya a 'ya geçirildiğinde <xref:System.ServiceModel.ChannelFactory%601> , WCF, arabirimdeki öznitelikleri inceler. Herhangi bir öznitelik uygulama ise <xref:System.ServiceModel.Description.IContractBehavior> , bunlar bu <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> arabirim için oluşturulan davranışlar koleksiyonuna eklenir.  
  
 Ayrıca, <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> özel sözleşme davranışı özniteliğinde öğesini de uygulayabilirsiniz. Bu durumda, davranış şu şekilde uygulandığında aşağıdaki gibidir:  
  
 • Bir sözleşme arabirimi. Bu durumda, davranış herhangi bir uç noktada bu türün tüm sözleşmelerine uygulanır ve WCF özelliğin değerini yoksayar <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> .  
  
 • Bir hizmet sınıfı. Bu durumda, davranışı yalnızca sözleşmesinin özelliğin değeri olan bitiş noktalarına uygulanır <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> .  
  
 • Bir geri çağırma sınıfı. Bu durumda, davranış çift yönlü istemcinin uç noktasına uygulanır ve WCF özelliğin değerini yoksayar <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> .  
  
 İkinci mekanizma, davranışını bir üzerinde davranışlar koleksiyonuna eklemektir <xref:System.ServiceModel.Description.ContractDescription> .  
  
 WCF 'deki sözleşme davranışları örnekleri <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> özniteliği içerir. Daha fazla bilgi ve bir örnek için bkz. başvuru konusu.  
  
#### <a name="endpoint-behaviors"></a>Uç nokta davranışları  
 Uygulayan uç nokta davranışları, <xref:System.ServiceModel.Description.IEndpointBehavior> belirli bir uç nokta için tüm hizmet veya istemci çalışma süresini değiştirdiğiniz birincil mekanizmadır.  
  
 Bir hizmete Endpoint davranışları eklemek için iki mekanizma vardır.  
  
1. <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A>Özelliği özelliğine ekleyin.  
  
2. Yapılandırmayı genişleten özel bir özel uygulama uygulayın <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> .  
  
 Daha fazla bilgi ve bir örnek için bkz. başvuru konusu.  
  
#### <a name="operation-behaviors"></a>İşlem davranışları  
 Arabirimini uygulayan işlem davranışları, <xref:System.ServiceModel.Description.IOperationBehavior> her bir işlem için hem istemci hem de hizmet çalışma zamanını genişletmek için kullanılır.  
  
 Bir işleme işlem davranışları eklemek için iki mekanizma vardır. İlk mekanizma, işlemi modelleyen yöntemde kullanılacak özel bir öznitelik oluşturmaktır. Bir veya bir öğesine bir işlem eklendiğinde <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ChannelFactory> , WCF <xref:System.ServiceModel.Description.IOperationBehavior> <xref:System.ServiceModel.Description.OperationDescription> Bu işlem için oluşturulan davranış koleksiyonuna herhangi bir öznitelik ekler.  
  
 İkinci mekanizma, davranışı oluşturulan davranış koleksiyonuna doğrudan eklemektir <xref:System.ServiceModel.Description.OperationDescription> .  
  
 WCF 'de işlem davranışlarının örnekleri, <xref:System.ServiceModel.OperationBehaviorAttribute> ve ' i içerir <xref:System.ServiceModel.TransactionFlowAttribute> .  
  
 Daha fazla bilgi ve bir örnek için bkz. başvuru konusu.  
  
### <a name="using-configuration-to-create-behaviors"></a>Davranışları oluşturmak için yapılandırma kullanma  
 Hizmet ve uç nokta ve sözleşme davranışları, kodda veya öznitelikler kullanılarak belirtime göre tasarlanmış olabilir; yalnızca hizmet ve uç nokta davranışları, uygulama veya Web yapılandırma dosyaları kullanılarak yapılandırılabilir. Öznitelikleri kullanarak davranışları göstermek, geliştiricilerin, çalışma zamanında eklenemeyen, kaldırılamayan veya değiştirilemeyen derleme zamanında bir davranış belirtmesini sağlar. Bu, genellikle bir hizmetin doğru çalışması için her zaman gerekli olan davranışlar için uygundur (örneğin, özniteliğe yönelik işlem ile ilgili parametreler <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> ). Yapılandırma kullanarak davranışları göstermek, geliştiricilerin bu davranışların belirtimini ve yapılandırmalarını hizmeti dağıtan kullanıcılara bırakmasını sağlar. Bu, isteğe bağlı bileşenler veya hizmet için meta verilerin sunulup sunulmadığı veya bir hizmetin belirli yetkilendirme yapılandırması gibi dağıtıma özgü bir yapılandırma olan davranışlar için uygundur.  
  
> [!NOTE]
> Ayrıca, machine.config yapılandırma dosyasına ekleyerek ve bu öğeleri aşağı kilitleyerek şirket uygulama ilkelerini zorlamak için yapılandırmayı destekleyen davranışları kullanabilirsiniz. Bir açıklama ve örnek için bkz. [nasıl yapılır: kuruluştaki uç noktaları kilitleme](how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Yapılandırma kullanarak bir davranışı ortaya çıkarmak için, geliştiricinin türetilmiş bir sınıfını oluşturması <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> ve sonra bu uzantıyı yapılandırmayla kaydetmesi gerekir.  
  
 Aşağıdaki kod örneğinde nasıl bir uyguladığı gösterilmektedir <xref:System.ServiceModel.Description.IEndpointBehavior> <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> :  
  
```csharp
// BehaviorExtensionElement members  
public override Type BehaviorType  
{  
  get { return typeof(EndpointBehaviorMessageInspector); }  
}  
  
protected override object CreateBehavior()  
{  
  return new EndpointBehaviorMessageInspector();  
}  
```  
  
 Yapılandırma sisteminin özel yüklemesi için bir <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> uzantı olarak kaydedilmesi gerekir. Aşağıdaki kod örneği, önceki uç nokta davranışı için yapılandırma dosyasını gösterir:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Burada `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` davranış uzantısı türüdür ve `HostApplication` Bu sınıfın derlenmiş olduğu derlemenin adıdır.  
  
### <a name="evaluation-order"></a>Değerlendirme sırası  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>Ve, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> programlama modelinden ve açıklamasında çalışma zamanının oluşturulmasından sorumludur. Davranışlar, daha önce açıklandığı gibi hizmet, uç nokta, sözleşme ve işlem ile ilgili derleme sürecine katkıda bulunur.  
  
 <xref:System.ServiceModel.ServiceHost>Aşağıdaki sırayla davranışları uygular:  
  
1. Hizmet  
  
2. Sözleşme  
  
3. Uç Nokta  
  
4. Çalışma  
  
 Herhangi bir davranış koleksiyonunda hiçbir sıra garanti edilmez.  
  
 <xref:System.ServiceModel.ChannelFactory%601>Aşağıdaki sırayla davranışları uygular:  
  
1. Sözleşme  
  
2. Uç Nokta  
  
3. Çalışma  
  
 Herhangi bir davranış koleksiyonu içinde, bir sıra garanti edilmez.  
  
### <a name="adding-behaviors-programmatically"></a>Program aracılığıyla davranış ekleme  
 Hizmet uygulamasındaki öğesinin özellikleri, <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> üzerindeki yöntemine sonradan değiştirilmemelidir <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> . Özelliği ve içindeki yöntemleri gibi bazı üyeler, <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> `AddServiceEndpoint` <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> o noktadan sonra değiştirilirse bir özel durum oluşturur. Diğerleri bunları değiştirmenize izin verir, ancak sonuç tanımsızdır.  
  
 Benzer şekilde, istemcide, <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> üzerine çağrısından sonra değerler değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> . <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType>Özelliği, o noktadan sonra değiştirilirse bir özel durum oluşturur, ancak diğer istemci açıklama değerleri hatasız şekilde değiştirilebilir. Ancak sonuç tanımsızdır.  
  
 Hizmet veya istemci için, çağrılmadan önce açıklamayı değiştirmeniz önerilir <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> .  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Davranış öznitelikleri için devralma kuralları  
 Dört tür davranışların tümü, öznitelikler – hizmet davranışları ve sözleşme davranışları kullanılarak doldurulabilir. Öznitelikler yönetilen nesneler ve Üyeler üzerinde tanımlandığından ve yönetilen nesneler ve Üyeler devralmayı desteklediğinden, davranış özniteliklerinin devralma bağlamında nasıl çalıştığını tanımlamanız gerekir.  
  
 Yüksek düzeyde, kural belirli bir kapsam (örneğin, hizmet, anlaşma veya işlem) için, bu kapsamın devralma hiyerarşisindeki tüm davranış özniteliklerinin uygulandığı bir işlemdir. Aynı türde iki davranış özniteliği varsa, yalnızca en fazla türetilmiş tür kullanılır.  
  
#### <a name="service-behaviors"></a>Hizmet davranışları  
 Belirli bir hizmet sınıfı için, bu sınıftaki ve bu sınıfın üst öğelerinin tüm hizmet davranışı öznitelikleri uygulanır. Devralma hiyerarşisinde aynı öznitelik türü birden fazla yerde uygulanırsa, en fazla türetilmiş tür kullanılır.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Örneğin, bir önceki durumda, hizmet B, ' ın bir <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.Single> modu, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ve ' ı <xref:System.ServiceModel.ConcurrencyMode> ile biter <xref:System.ServiceModel.ConcurrencyMode.Single> . , <xref:System.ServiceModel.ConcurrencyMode> <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ServiceBehaviorAttribute> Hizmet B 'Deki özniteliği, A hizmetindeki "daha fazla türetilmiş" üzerinde olduğundan.  
  
#### <a name="contract-behaviors"></a>Sözleşme davranışları  
 Belirli bir sözleşme için, bu arabirimdeki ve bu arabirimin üst öğelerinden tüm sözleşme davranışı öznitelikleri uygulanır. Devralma hiyerarşisinde aynı öznitelik türü birden fazla yerde uygulanırsa, en fazla türetilmiş tür kullanılır.  
  
#### <a name="operation-behaviors"></a>İşlem davranışları  
 Belirli bir işlem varolan bir soyut veya sanal işlemi geçersiz kılamaz devralma kuralı uygulanmaz.  
  
 Bir işlem varolan bir işlemi geçersiz kılarsa bu işlem üzerindeki tüm işlem davranışı öznitelikleri ve bu işlemin üst öğeleri uygulanır.  Devralma hiyerarşisinde aynı öznitelik türü birden fazla yerde uygulanırsa, en fazla türetilmiş tür kullanılır.
