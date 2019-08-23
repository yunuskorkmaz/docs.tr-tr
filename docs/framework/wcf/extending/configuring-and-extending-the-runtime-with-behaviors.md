---
title: Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 481e0983a40bb551d08894ea32f76f332b8fe5a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943134"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
Davranışlar, varsayılan davranışı değiştirmenize ve Windows Communication Foundation (WCF) istemci ve hizmet uygulamalarında hizmet yapılandırmasını incelemek ve doğrulamak veya çalışma zamanı davranışını değiştirmek için özel uzantılar eklemenize olanak tanır. Bu konu, davranış arabirimlerini, bunların nasıl uygulanacağını ve hizmet açıklamasına (bir hizmet uygulamasına) veya uç noktaya (bir istemci uygulamasında) program aracılığıyla veya bir yapılandırma dosyasına nasıl ekleneceğini açıklar. Sistem tarafından sunulan davranışları kullanma hakkında daha fazla bilgi için bkz. [hizmet çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) ve [Istemci çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Davranışlar  
 Davranış türleri, hizmet veya hizmet uç noktası açıklaması nesnelerine (sırasıyla hizmet veya istemci), bu nesneler bir WCF hizmetini veya WCF istemcisini yürüten bir çalışma zamanı oluşturmak için Windows Communication Foundation (WCF) tarafından kullanılmadan önce eklenir. Çalışma zamanı oluşturma işlemi sırasında bu davranışlar çağrıldığında, çalışma zamanı özelliklerine ve anlaşma, bağlamalar ve adresler tarafından oluşturulan çalışma zamanını değiştiren yöntemlere erişebilecektir.  
  
### <a name="behavior-methods"></a>Davranış yöntemleri  
 Tüm davranışlar bir `AddBindingParameters` yönteme `ApplyDispatchBehavior` , yönteme, `Validate` yönteme ve bir özel duruma sahip bir `ApplyClientBehavior` yönteme sahiptir: Bir istemcide `ApplyClientBehavior`yürütülemediğinden, uygulamaz. <xref:System.ServiceModel.Description.IServiceBehavior>  
  
- Özel bağlamaların çalışma zamanı oluşturulduğunda kullanımları için erişebileceği bir koleksiyona özel nesneler eklemek veya değiştirmek için yönteminikullanın.`AddBindingParameters` Örneğin, bu, kanalın oluşturulduğu, ancak kanal geliştiricisi tarafından bilinmediği, koruma gereksinimlerinin nasıl belirtileceğine ilişkin bir yöntemdir.  
  
- Bir dizi ölçüte uyduğundan emin olmak için açıklama ağacını ve ilgili çalışma zamanı nesnesini incelemek üzere yönteminikullanın.`Validate`  
  
- `ApplyDispatchBehavior` Ve`ApplyClientBehavior` yöntemleri, açıklama ağacını incelemek ve hizmet ya da istemcide belirli bir kapsamın çalışma zamanını değiştirmek için kullanın. Ayrıca uzantı nesneleri de ekleyebilirsiniz.  
  
    > [!NOTE]
    > Bu yöntemlerde bir açıklama ağacı sağlanmış olsa da, yalnızca İnceleme amaçlıdır. Bir açıklama ağacı değiştirilirse, davranış tanımsızdır.  
  
 Değiştirebileceğiniz özelliklere ve uygulayabileceğiniz özelleştirme arabirimlerine hizmet ve istemci çalışma zamanı sınıfları üzerinden erişilir. Hizmet türleri <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıflarıdır. İstemci türleri <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.ClientOperation> sınıflarıdır. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Ve<xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfları, sırasıyla istemci genelindeki ve hizmet genelindeki çalışma zamanı özelliklerine ve uzantı koleksiyonlarına erişmek için genişletilebilirlik giriş noktalarıdır. Benzer şekilde, <xref:System.ServiceModel.Dispatcher.DispatchOperation>vesınıfları sırasıyla istemci işlemini ve hizmet işlemi çalışma zamanı özelliklerini ve uzantı koleksiyonlarını da kullanıma sunar. <xref:System.ServiceModel.Dispatcher.ClientOperation> Ancak, daha geniş kapsamlı çalışma zamanı nesnesine işlem çalışma zamanı nesnesinden erişebilir ve gerekirse bunun tersini yapabilirsiniz.  
  
> [!NOTE]
> Bir istemcinin yürütme davranışını değiştirmek için kullanabileceğiniz çalışma zamanı özellikleri ve uzantı türleri hakkında bir tartışma için bkz. [Istemcileri genişletme](../../../../docs/framework/wcf/extending/extending-clients.md). Bir hizmet dağıtıcısı 'nin yürütme davranışını değiştirmek için kullanabileceğiniz çalışma zamanı özellikleri ve uzantı türleri hakkında bir tartışma için bkz. [dispatchers 'ı genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
 Çoğu WCF kullanıcısı çalışma zamanında doğrudan etkileşime girmez; Bunun yerine, yapılandırma dosyalarındaki sınıflarda veya davranışlarda uç noktalar, sözleşmeler, bağlamalar, adresler ve davranış öznitelikleri gibi temel programlama modeli yapılarını kullanırlar. Bu yapılar, açıklama ağacı tarafından tanımlanan bir hizmet veya istemciyi desteklemek için bir çalışma zamanı oluşturma belirtiminin tamamı olan *Açıklama ağacını*oluşturur.  
  
 WCF 'de dört tür davranış vardır:  
  
- Hizmet davranışları (<xref:System.ServiceModel.Description.IServiceBehavior> türler), dahil olmak üzere <xref:System.ServiceModel.ServiceHostBase>tüm hizmet çalışma zamanının özelleştirilmesini etkinleştirir.  
  
- Uç nokta davranışları<xref:System.ServiceModel.Description.IEndpointBehavior> (türler) hizmet uç noktalarının ve bunlarla ilişkili <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesnelerin özelleştirilmesini etkinleştirir.  
  
- Anlaşma davranışları (<xref:System.ServiceModel.Description.IContractBehavior> türler), sırasıyla istemci ve hizmet uygulamalarında <xref:System.ServiceModel.Dispatcher.ClientRuntime> hem <xref:System.ServiceModel.Dispatcher.DispatchRuntime> hem de sınıflarının özelleştirilmesini etkinleştirir.  
  
- İşlem davranışları (<xref:System.ServiceModel.Description.IOperationBehavior> türler), <xref:System.ServiceModel.Dispatcher.ClientOperation> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıflarının özelleştirmesini, istemci ve hizmette yeniden etkinleştirir.  
  
 Bu davranışları çeşitli açıklama nesnelerine, uygulama yapılandırma dosyalarını kullanarak veya doğrudan ilgili açıklama nesnesindeki davranışlar koleksiyonuna ekleyerek ekleyebilirsiniz. Ancak, <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost> veya ' a <xref:System.ServiceModel.ChannelFactory%601>çağrılmadan önce bir hizmet açıklamasına veya hizmet uç noktası açıklama nesnesine eklenmelidir.  
  
### <a name="behavior-scopes"></a>Davranış kapsamları  
 Her biri çalışma zamanı erişiminin belirli bir kapsamına karşılık gelen dört davranış türü vardır.  
  
#### <a name="service-behaviors"></a>Hizmet davranışları  
 Hizmetini uygulayan <xref:System.ServiceModel.Description.IServiceBehavior>hizmet davranışları, hizmet çalışma zamanının tamamını değiştirdiğiniz birincil mekanizmadır. Hizmete hizmet davranışları eklemek için üç mekanizma vardır.  
  
1. Hizmet sınıfında bir özniteliği kullanılıyor.  Bir <xref:System.ServiceModel.ServiceHost> oluşturulduğunda<xref:System.ServiceModel.ServiceHost> , uygulama, hizmet türündeki öznitelik kümesini saptamak için yansıma kullanır. Bu özniteliklerden herhangi biri uygulamalarsa <xref:System.ServiceModel.Description.IServiceBehavior>, üzerindeki <xref:System.ServiceModel.Description.ServiceDescription>davranışlar koleksiyonuna eklenir. Bu, bu davranışların hizmet çalışma zamanının oluşturulmasına katılmasına izin verir.  
  
2. Davranışı ' de <xref:System.ServiceModel.Description.ServiceDescription>davranış koleksiyonuna programlı bir şekilde ekleme. Bu, aşağıdaki kod satırlarıyla gerçekleştirilebilir:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Yapılandırmayı genişleten özel <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> bir uygulama. Bu, uygulama yapılandırma dosyalarından hizmet davranışının kullanılmasına izin vermez.  
  
 WCF 'de hizmet davranışlarına örnek <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>olarak öznitelik,, ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı dahildir.  
  
#### <a name="contract-behaviors"></a>Sözleşme davranışları  
 <xref:System.ServiceModel.Description.IContractBehavior> Arabirimini uygulayan sözleşme davranışları, hem istemci hem de hizmet çalışma zamanını bir sözleşme genelinde genişletmek için kullanılır.  
  
 Sözleşmeye sözleşme davranışları eklemek için iki mekanizma vardır.  İlk mekanizma, sözleşme arabiriminde kullanılacak özel bir öznitelik oluşturmaktır. Bir sözleşme arabirimi bir <xref:System.ServiceModel.ServiceHost> veya a <xref:System.ServiceModel.ChannelFactory%601>'ya geçirildiğinde, WCF, arabirimdeki öznitelikleri inceler. Herhangi bir öznitelik uygulama <xref:System.ServiceModel.Description.IContractBehavior>ise, bunlar bu arabirim için <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> oluşturulan davranışlar koleksiyonuna eklenir.  
  
 Ayrıca, <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> özel sözleşme davranışı özniteliğinde öğesini de uygulayabilirsiniz. Bu durumda, davranış şu şekilde uygulandığında aşağıdaki gibidir:  
  
 • Bir sözleşme arabirimi. Bu durumda, davranış herhangi bir uç noktada bu türün tüm sözleşmelerine uygulanır ve WCF <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> özelliğin değerini yoksayar.  
  
 • Bir hizmet sınıfı. Bu durumda, davranışı yalnızca sözleşmesinin <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> özelliğin değeri olan bitiş noktalarına uygulanır.  
  
 • Bir geri çağırma sınıfı. Bu durumda, davranış çift yönlü istemcinin uç noktasına uygulanır ve WCF <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> özelliğin değerini yoksayar.  
  
 İkinci mekanizma, davranışını bir <xref:System.ServiceModel.Description.ContractDescription>üzerinde davranışlar koleksiyonuna eklemektir.  
  
 WCF 'deki sözleşme davranışları örnekleri <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> özniteliği içerir. Daha fazla bilgi ve bir örnek için bkz. başvuru konusu.  
  
#### <a name="endpoint-behaviors"></a>Uç nokta davranışları  
 Uygulayan <xref:System.ServiceModel.Description.IEndpointBehavior>uç nokta davranışları, belirli bir uç nokta için tüm hizmet veya istemci çalışma süresini değiştirdiğiniz birincil mekanizmadır.  
  
 Bir hizmete Endpoint davranışları eklemek için iki mekanizma vardır.  
  
1. <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> Özelliği özelliğine ekleyin.  
  
2. Yapılandırmayı genişleten özel <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> bir özel uygulama uygulayın.  
  
 Daha fazla bilgi ve bir örnek için bkz. başvuru konusu.  
  
#### <a name="operation-behaviors"></a>İşlem davranışları  
 <xref:System.ServiceModel.Description.IOperationBehavior> Arabirimini uygulayan işlem davranışları, her bir işlem için hem istemci hem de hizmet çalışma zamanını genişletmek için kullanılır.  
  
 Bir işleme işlem davranışları eklemek için iki mekanizma vardır. İlk mekanizma, işlemi modelleyen yöntemde kullanılacak özel bir öznitelik oluşturmaktır. Bir <xref:System.ServiceModel.ServiceHost> veya bir <xref:System.ServiceModel.ChannelFactory>öğesine bir işlem eklendiğinde, WCF bu işlem için <xref:System.ServiceModel.Description.OperationDescription> oluşturulan davranış <xref:System.ServiceModel.Description.IOperationBehavior> koleksiyonuna herhangi bir öznitelik ekler.  
  
 İkinci mekanizma, davranışı oluşturulan <xref:System.ServiceModel.Description.OperationDescription>davranış koleksiyonuna doğrudan eklemektir.  
  
 WCF 'de işlem davranışlarının örnekleri, <xref:System.ServiceModel.OperationBehaviorAttribute> <xref:System.ServiceModel.TransactionFlowAttribute>ve ' i içerir.  
  
 Daha fazla bilgi ve bir örnek için bkz. başvuru konusu.  
  
### <a name="using-configuration-to-create-behaviors"></a>Davranışları oluşturmak için yapılandırma kullanma  
 Hizmet ve uç nokta ve sözleşme davranışları, kodda veya öznitelikler kullanılarak belirtime göre tasarlanmış olabilir; yalnızca hizmet ve uç nokta davranışları, uygulama veya Web yapılandırma dosyaları kullanılarak yapılandırılabilir. Öznitelikleri kullanarak davranışları göstermek, geliştiricilerin, çalışma zamanında eklenemeyen, kaldırılamayan veya değiştirilemeyen derleme zamanında bir davranış belirtmesini sağlar. Bu, genellikle bir hizmetin doğru çalışması için her zaman gerekli olan davranışlar için uygundur (örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> özniteliğe yönelik işlem ile ilgili parametreler). Yapılandırma kullanarak davranışları göstermek, geliştiricilerin bu davranışların belirtimini ve yapılandırmalarını hizmeti dağıtan kullanıcılara bırakmasını sağlar. Bu, isteğe bağlı bileşenler veya hizmet için meta verilerin sunulup sunulmadığı veya bir hizmetin belirli yetkilendirme yapılandırması gibi dağıtıma özgü bir yapılandırma olan davranışlar için uygundur.  
  
> [!NOTE]
> Ayrıca, şirket uygulama ilkelerini Machine. config yapılandırma dosyasına ekleyerek ve bu öğeleri aşağı kilitleyerek, şirket uygulama ilkelerini zorlamak için yapılandırmayı destekleyen davranışları kullanabilirsiniz. Bir açıklama ve örnek için bkz [. nasıl yapılır: Kuruluştaki](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)uç noktaları kilitle.  
  
 Yapılandırma kullanarak bir davranışı ortaya çıkarmak için, geliştiricinin türetilmiş bir sınıfını <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> oluşturması ve sonra bu uzantıyı yapılandırmayla kaydetmesi gerekir.  
  
 Aşağıdaki kod örneğinde nasıl bir <xref:System.ServiceModel.Description.IEndpointBehavior> uyguladığı <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>gösterilmektedir:  
  
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
  
 Yapılandırma sisteminin özel <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>yüklemesi için bir uzantı olarak kaydedilmesi gerekir. Aşağıdaki kod örneği, önceki uç nokta davranışı için yapılandırma dosyasını gösterir:  
  
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
  
 Burada `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` davranış uzantısı türüdür ve `HostApplication` bu sınıfın derlenmiş olduğu derlemenin adıdır.  
  
### <a name="evaluation-order"></a>Değerlendirme sırası  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> Ve ,<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> programlama modelinden ve açıklamasında çalışma zamanının oluşturulmasından sorumludur. Davranışlar, daha önce açıklandığı gibi hizmet, uç nokta, sözleşme ve işlem ile ilgili derleme sürecine katkıda bulunur.  
  
 Aşağıdaki sırayla davranışları uygular: <xref:System.ServiceModel.ServiceHost>  
  
1. Hizmet  
  
2. Sözleşme  
  
3. Uç Noktası  
  
4. Çalışma  
  
 Herhangi bir davranış koleksiyonunda hiçbir sıra garanti edilmez.  
  
 Aşağıdaki sırayla davranışları uygular: <xref:System.ServiceModel.ChannelFactory%601>  
  
1. Sözleşme  
  
2. Uç Noktası  
  
3. Çalışma  
  
 Herhangi bir davranış koleksiyonu içinde, bir sıra garanti edilmez.  
  
### <a name="adding-behaviors-programmatically"></a>Program aracılığıyla davranış ekleme  
 Hizmet uygulamasındaki öğesinin <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> özellikleri, üzerindeki <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>yöntemine sonradan değiştirilmemelidir. <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> Özelliği <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> veiçindeki<xref:System.ServiceModel.ServiceHostBase>yöntemlerigibi bazı üyeler, o noktadan sonra değiştirilirse bir özel durum oluşturur. `AddServiceEndpoint` Diğerleri bunları değiştirmenize izin verir, ancak sonuç tanımsızdır.  
  
 Benzer şekilde, istemcide <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> , <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerine <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>çağrısından sonra değerler değiştirilmemelidir. <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> Özelliği, o noktadan sonra değiştirilirse bir özel durum oluşturur, ancak diğer istemci açıklama değerleri hatasız şekilde değiştirilebilir. Ancak sonuç tanımsızdır.  
  
 Hizmet veya istemci için, çağrılmadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>önce açıklamayı değiştirmeniz önerilir.  
  
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
  
 Örneğin, bir önceki durumda, hizmet B, ' ın <xref:System.ServiceModel.InstanceContextMode> bir <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.InstanceContextMode.Single> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> modu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, ve <xref:System.ServiceModel.ConcurrencyMode> ' ı ile biter. ,HizmetB'dekiözniteliği,Ahizmetindeki"dahafazlatüretilmiş"üzerindeolduğundan.<xref:System.ServiceModel.ConcurrencyMode> <xref:System.ServiceModel.ConcurrencyMode.Single> <xref:System.ServiceModel.ServiceBehaviorAttribute>  
  
#### <a name="contract-behaviors"></a>Sözleşme davranışları  
 Belirli bir sözleşme için, bu arabirimdeki ve bu arabirimin üst öğelerinden tüm sözleşme davranışı öznitelikleri uygulanır. Devralma hiyerarşisinde aynı öznitelik türü birden fazla yerde uygulanırsa, en fazla türetilmiş tür kullanılır.  
  
#### <a name="operation-behaviors"></a>İşlem davranışları  
 Belirli bir işlem varolan bir soyut veya sanal işlemi geçersiz kılamaz devralma kuralı uygulanmaz.  
  
 Bir işlem varolan bir işlemi geçersiz kılarsa bu işlem üzerindeki tüm işlem davranışı öznitelikleri ve bu işlemin üst öğeleri uygulanır.  Devralma hiyerarşisinde aynı öznitelik türü birden fazla yerde uygulanırsa, en fazla türetilmiş tür kullanılır.
