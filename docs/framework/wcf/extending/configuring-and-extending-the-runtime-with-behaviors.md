---
title: Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 67db06649d6059ff6b6e6fb8d84058621fcc7dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185650"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
Davranışlar, Windows Communication Foundation (WCF) istemci ve hizmet uygulamalarında varsayılan davranışı değiştirmenize ve hizmet yapılandırmasını denetleyen ve doğrulayan veya çalışma zamanı davranışını değiştiren özel uzantılar eklemenize olanak tanır. Bu konu davranış arabirimlerini, bunların nasıl uygulanacağını ve bunları hizmet açıklamasına (hizmet uygulamasında) veya bitiş noktasına (istemci uygulamasında) programlı olarak veya yapılandırma dosyasına nasıl ekleyeceğini açıklar. Sistem tarafından sağlanan davranışları kullanma hakkında daha fazla bilgi için [Specifying Client Run-Time Behavior](../specifying-client-run-time-behavior.md) [bkz.](../specifying-service-run-time-behavior.md)  
  
## <a name="behaviors"></a>Davranışlar  
 Davranış türleri, bu nesneler Windows Communication Foundation (WCF) tarafından wcf hizmeti veya WCF istemcisi çalıştıran bir çalışma zamanı oluşturmak için kullanılmadan önce hizmet veya hizmet bitiş noktası açıklama nesnelerine (sırasıyla hizmet veya istemcide) eklenir. Bu davranışlar çalışma zamanı inşaat işlemi sırasında çağrıldığında, sözleşme, bağlamalar ve adresler tarafından oluşturulmuş çalışma süresini değiştiren çalışma zamanı özelliklerine ve yöntemlerine erişebilirler.  
  
### <a name="behavior-methods"></a>Davranış Yöntemleri  
 Tüm davranışların `AddBindingParameters` bir yöntemi, yöntemi, `ApplyDispatchBehavior` `Validate` yöntemi `ApplyClientBehavior` ve bir özel <xref:System.ServiceModel.Description.IServiceBehavior> durum olan bir yöntemi vardır: `ApplyClientBehavior`İstemcide yürütülemediği için, uygulamaz.  
  
- Özel `AddBindingParameters` bağlamaların çalışma zamanı oluşturulduğunda kullanımları için erişebileceği bir koleksiyona özel nesneleri değiştirmek veya eklemek için yöntemi kullanın. Örneğin, bu şekilde koruma gereksinimleri kanal inşa şeklini etkileyen belirtilir, ancak kanal geliştiricisi tarafından bilinmemektedir.  
  
- Bazı `Validate` ölçütlere uyduklarından emin olmak için açıklama ağacını ve ilgili çalışma zamanı nesnesini incelemek için yöntemi kullanın.  
  
- Açıklama `ApplyDispatchBehavior` ağacını incelemek ve hizmet veya istemci üzerinde belirli bir kapsam için çalışma zamanını değiştirmek için ve `ApplyClientBehavior` yöntemleri kullanın. Uzantı nesnelerini de ekleyebilirsiniz.  
  
    > [!NOTE]
    > Bu yöntemlerde bir açıklama ağacı sağlanmış olsa da, yalnızca inceleme içindir. Açıklama ağacı değiştirilirse, davranış tanımsız.  
  
 Değiştirebileceğiniz özellikler ve uygulayabileceğiniz özelleştirme arabirimleri, hizmet ve istemci çalışma zamanı sınıfları aracılığıyla erişilir. Hizmet türleri <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıflardır. İstemci türleri <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.ClientOperation> ve sınıflardır. Ve <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıflar, sırasıyla istemci genelinde ve hizmet genelinde çalışma süresi özelliklerine ve uzantı koleksiyonlarına erişmek için genişletilebilirlik giriş noktalarıdır. Benzer şekilde, <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> ve sınıflar sırasıyla istemci çalışma ve hizmet çalışma zamanı özelliklerini ve uzantı koleksiyonlarını ortaya çıkarır. Ancak, işlem çalışma zamanı nesnesinden daha geniş kapsamlı çalışma zamanı nesnesi ve gerekirse tam tersi erişebilirsiniz.  
  
> [!NOTE]
> İstemcinin yürütme davranışını değiştirmek için kullanabileceğiniz çalışma zamanı özellikleri ve uzantı türlerinin tartışılması için [bkz.](extending-clients.md) Bir hizmet dağıtıcısının yürütme davranışını değiştirmek için kullanabileceğiniz çalışma zamanı özellikleri ve uzantı türlerinin tartışılması için [bkz.](extending-dispatchers.md)  
  
 WCF kullanıcılarının çoğu çalışma zamanıyla doğrudan etkileşime girmez; bunun yerine, yapılandırma dosyalarındaki sınıflar veya davranışlar da dahil olmak üzere uç noktalar, sözleşmeler, bağlamalar, adresler ve davranış öznitelikleri gibi temel programlama modeli yapılarını kullanırlar. Bu yapılar, açıklama ağacı tarafından açıklanan bir hizmeti veya istemciyi desteklemek için bir çalışma zamanı oluşturmak için tam belirtimi olan *açıklama ağacını*oluşturuyor.  
  
 WCF'de dört tür davranış vardır:  
  
- Hizmet davranışları<xref:System.ServiceModel.Description.IServiceBehavior> (türleri) dahil olmak üzere tüm hizmet <xref:System.ServiceModel.ServiceHostBase>çalışma süresiözelleştirme sağlar.  
  
- Uç nokta davranışları<xref:System.ServiceModel.Description.IEndpointBehavior> (türleri) hizmet bitiş noktaları nın <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> ve ilişkili nesnelerin özelleştirilmesini sağlar.  
  
- Sözleşme davranışları<xref:System.ServiceModel.Description.IContractBehavior> (türleri), sırasıyla istemci <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> hizmet uygulamalarında hem sınıfların hem de sınıfların özelleştirilmesini sağlar.  
  
- İşlem davranışları<xref:System.ServiceModel.Description.IOperationBehavior> (türleri), istemci <xref:System.ServiceModel.Dispatcher.ClientOperation> ve hizmet <xref:System.ServiceModel.Dispatcher.DispatchOperation> üzerinde yine sınıfların ve sınıfların özelleştirilmesini sağlar.  
  
 Bu davranışları, özel öznitelikleri uygulayarak, uygulama yapılandırma dosyalarını kullanarak veya doğrudan uygun açıklama nesnesindeki davranış koleksiyonuna ekleyerek çeşitli açıklama nesnelerine ekleyebilirsiniz. Ancak, bir hizmet açıklaması na veya hizmet bitiş noktası açıklaması <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost> nesnesine, <xref:System.ServiceModel.ChannelFactory%601>bir hizmeti veya bir .  
  
### <a name="behavior-scopes"></a>Davranış Kapsamları  
 Her biri belirli bir çalışma zamanı erişim kapsamına karşılık gelen dört davranış türü vardır.  
  
#### <a name="service-behaviors"></a>Hizmet Davranışları  
 Uygulayan <xref:System.ServiceModel.Description.IServiceBehavior>hizmet davranışları, tüm hizmet çalışma süresini değiştirdiğiniz birincil mekanizmadır. Bir hizmete hizmet davranışları eklemek için üç mekanizma vardır.  
  
1. Hizmet sınıfında bir öznitelik kullanma.  Bir <xref:System.ServiceModel.ServiceHost> oluşturulduğunda, <xref:System.ServiceModel.ServiceHost> uygulama hizmet türüne ilişkin öznitelikler kümesini keşfetmek için yansımayı kullanır. Bu özniteliklerden <xref:System.ServiceModel.Description.IServiceBehavior>herhangi biri , davranış koleksiyonuna <xref:System.ServiceModel.Description.ServiceDescription>eklenir. Bu, bu davranışların hizmet çalışma süresinin yapımına katılmasını sağlar.  
  
2. Davranışları n için programlı olarak <xref:System.ServiceModel.Description.ServiceDescription>ekleme. Bu kod aşağıdaki satırları ile gerçekleştirilebilir:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Yapılandırmayı genişleten bir özel <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> uygulama. Bu, uygulama yapılandırma dosyalarından hizmet davranışının kullanılmasını sağlar.  
  
 WCF'deki hizmet davranışlarına <xref:System.ServiceModel.ServiceBehaviorAttribute> örnek olarak <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>öznitelik, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ve davranış verilebilir.  
  
#### <a name="contract-behaviors"></a>Sözleşme Davranışları  
 <xref:System.ServiceModel.Description.IContractBehavior> Arabirimi uygulayan sözleşme davranışları, hem istemciyi hem de hizmet çalışma süresini sözleşme boyunca genişletmek için kullanılır.  
  
 Sözleşme davranışları nın sözleşmeye eklenmesi için iki mekanizma vardır.  İlk mekanizma, sözleşme arabiriminde kullanılmak üzere özel bir öznitelik oluşturmaktır. Bir sözleşme arabirimi a <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601>a geçirildiğinde, WCF arabirimdeki öznitelikleri inceler. Herhangi bir öznitelik <xref:System.ServiceModel.Description.IContractBehavior>, bu arabirim için <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> oluşturulan davranış koleksiyonuna eklenir uygulamaları vardır.  
  
 Ayrıca özel sözleşme <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> davranış özniteliği üzerinde uygulayabilirsiniz. Bu durumda, davranış aşağıdaki gibi uygulanır:  
  
 •Bir sözleşme arabirimi. Bu durumda, davranış herhangi bir uç noktada bu tür tüm sözleşmeleruygulanır ve WCF <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> özelliğinin değerini yokserer.  
  
 •Bir hizmet sınıfı. Bu durumda, davranış yalnızca <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> sözleşme özelliğinin değeri olan bitiş noktaları için uygulanır.  
  
 •Geri arama sınıfı. Bu durumda, davranış çift yönlü istemcinin bitiş noktasına uygulanır ve WCF <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> özelliğin değerini yoksaçar.  
  
 İkinci mekanizma, davranışı bir <xref:System.ServiceModel.Description.ContractDescription>' deki davranış koleksiyonuna eklemektir.  
  
 WCF'deki sözleşme davranışlarına <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> örnek olarak öznitelik verilebilir. Daha fazla bilgi ve örnek için başvuru konusuna bakın.  
  
#### <a name="endpoint-behaviors"></a>Bitiş Noktası Davranışları  
 Uygulanan <xref:System.ServiceModel.Description.IEndpointBehavior>bitiş noktası davranışları, belirli bir bitiş noktası için tüm hizmet veya istemci çalışma süresini değiştirdiğiniz birincil mekanizmadır.  
  
 Bir hizmete uç nokta davranışları eklemek için iki mekanizma vardır.  
  
1. Davranışı <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliğe ekleyin.  
  
2. Yapılandırmayı <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> genişleten bir özel uygulayın.  
  
 Daha fazla bilgi ve örnek için başvuru konusuna bakın.  
  
#### <a name="operation-behaviors"></a>Operasyon Davranışları  
 <xref:System.ServiceModel.Description.IOperationBehavior> Arabirimi uygulayan işlem davranışları, her işlem için hem istemci hem de hizmet çalışma süresini genişletmek için kullanılır.  
  
 Bir işlem için işlem davranışları eklemek için iki mekanizma vardır. İlk mekanizma, işlemi modelleyen yöntemde kullanılacak özel bir öznitelik oluşturmaktır. Bir işlem bir veya <xref:System.ServiceModel.ServiceHost> bir <xref:System.ServiceModel.ChannelFactory>, WCF <xref:System.ServiceModel.Description.IOperationBehavior> bu işlem için <xref:System.ServiceModel.Description.OperationDescription> oluşturulan davranış koleksiyonuna herhangi bir öznitelikleri ekler eklendiğinde.  
  
 İkinci mekanizma, davranışı doğrudan oluşturulmuş <xref:System.ServiceModel.Description.OperationDescription>bir yapıdaki davranış koleksiyonuna eklemektir.  
  
 WCF'deki işlem davranışlarına <xref:System.ServiceModel.OperationBehaviorAttribute> örnek <xref:System.ServiceModel.TransactionFlowAttribute>olarak .  
  
 Daha fazla bilgi ve örnek için başvuru konusuna bakın.  
  
### <a name="using-configuration-to-create-behaviors"></a>Davranış Oluşturmak için Yapılandırmayı Kullanma  
 Hizmet ve bitiş noktası ve sözleşme davranışları kodda belirtilecek şekilde tasarlanabilir veya öznitelikleri ni kullanabilir; yalnızca hizmet ve uç nokta davranışları uygulama veya Web yapılandırma dosyaları kullanılarak yapılandırılabilir. Öznitelikleri kullanarak davranışları açığa çıkarmak, geliştiricilerin derleme zamanında eklenemez, kaldırılamayan veya çalışma zamanında değiştirilemeyen bir davranış belirtmelerine olanak tanır. Bu genellikle bir hizmetin doğru çalışması için her zaman gerekli olan davranışlar için uygundur <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> (örneğin, öznitelik için işlemle ilgili parametreler). Yapılandırmayı kullanarak davranışların açığa çıkarılması, geliştiricilerin bu davranışların belirtimini ve yapılandırmasını hizmeti dağıtanlara bırakmasına olanak tanır. Bu, isteğe bağlı bileşenler veya meta verilerin hizmete açıkta olup olmadığı veya bir hizmet için belirli yetkilendirme yapılandırması gibi dağıtıma özgü diğer yapılandırmalar için uygundur.  
  
> [!NOTE]
> Ayrıca, şirket uygulama ilkelerini machine.config yapılandırma dosyasına ekleyerek ve bu öğeleri kilitleyerek yapılandırmayı destekleyen davranışları da kullanabilirsiniz. Bir açıklama ve örnek için [bkz.](how-to-lock-down-endpoints-in-the-enterprise.md)  
  
 Yapılandırmayı kullanarak bir davranışı ortaya çıkarmak için, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> bir geliştiricinin türetilmiş bir sınıf oluşturması ve bu uzantıyı yapılandırmayla kaydetmesi gerekir.  
  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.Description.IEndpointBehavior> bir <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>uygulamanın nasıl uygulandığını gösterir:  
  
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
  
 Yapılandırma sisteminin özel <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>bir yük yüklemesi için, bir uzantı olarak kaydedilmesi gerekir. Aşağıdaki kod örneği, önceki bitiş noktası davranışı için yapılandırma dosyasını gösterir:  
  
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
  
 Davranış `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` uzantısı türü nerededir ve `HostApplication` bu sınıfın derlendiği derlemenin adıdır.  
  
### <a name="evaluation-order"></a>Değerlendirme Emri  
 Ve <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> programlama <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> modeli ve açıklamasından çalışma zamanı oluşturmak için sorumludur. Davranışlar, daha önce açıklandığı gibi, hizmet, bitiş noktası, sözleşme ve çalışma bu yapı sürecine katkıda bulunur.  
  
 Aşağıdaki <xref:System.ServiceModel.ServiceHost> sırada davranışları uygular:  
  
1. Hizmet  
  
2. Sözleşme  
  
3. Uç Nokta  
  
4. İşlem  
  
 Herhangi bir davranış koleksiyonunda, hiçbir sipariş garanti değildir.  
  
 Aşağıdaki <xref:System.ServiceModel.ChannelFactory%601> sırada davranışları uygular:  
  
1. Sözleşme  
  
2. Uç Nokta  
  
3. İşlem  
  
 Davranışların herhangi bir koleksiyon içinde, yine, hiçbir sipariş garanti edilir.  
  
### <a name="adding-behaviors-programmatically"></a>Davranışları Programlı Olarak Ekleme  
 Hizmet uygulamasındaki <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> özellikleri, 'deki <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>yöntemden sonra değiştirilmemelidir. Bazı üyeler, <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> özellik ve `AddServiceEndpoint` yöntemleri <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>gibi ve, bu noktadan geçmiş değiştirilirse bir özel durum atmak. Diğerleri bunları değiştirmenize izin verir, ancak sonuç tanımsızdır.  
  
 Benzer şekilde, istemcide <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> değerler <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> çağrıdan sonra <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>değiştirilmemelidir. Özellik, <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> bu noktadan sonra değiştirilirse bir özel durum oluşturur, ancak diğer istemci açıklaması değerleri hatasız değiştirilebilir. Ancak sonuç tanımsızdır.  
  
 Hizmet veya istemci için olsun, aramadan <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>önce açıklamayı değiştirmeniz önerilir.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Davranış Öznitelikleri için Devralma Kuralları  
 Hizmet davranışları ve sözleşme davranışları gibi öznitelikler kullanılarak dört davranış türü de doldurulabilir. Öznitelikler yönetilen nesneler ve üyeler üzerinde tanımlandıve yönetilen nesneler ve üyeler devralmayı desteklediğinden, davranış özniteliklerinin devralma bağlamında nasıl çalıştığını tanımlamak gerekir.  
  
 Yüksek düzeyde, kural belirli bir kapsam (örneğin, hizmet, sözleşme veya işlem) için, bu kapsam için devralma hiyerarşisindeki tüm davranış özniteliklerinin uygulandığıdır. Aynı türde iki davranış öznitelikleri varsa, yalnızca en çok türetilmiş tür kullanılır.  
  
#### <a name="service-behaviors"></a>Hizmet Davranışları  
 Belirli bir hizmet sınıfı için, o sınıftaki tüm hizmet davranışı öznitelikleri ve bu sınıfın ebeveynleri için uygulanır. Devralma hiyerarşisinde birden çok yerde aynı tür öznitelik uygulanırsa, en çok türetilmiş tür kullanılır.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Örneğin, önceki durumda, B hizmeti <xref:System.ServiceModel.InstanceContextMode> bir <xref:System.ServiceModel.InstanceContextMode.Single>ile biter , <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> bir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>modu <xref:System.ServiceModel.ConcurrencyMode> , <xref:System.ServiceModel.ConcurrencyMode.Single>ve a . <xref:System.ServiceModel.ServiceBehaviorAttribute> Çünkü Hizmet B özniteliği hizmet A daha "daha fazla türetilmiş" üzerindedir. <xref:System.ServiceModel.ConcurrencyMode> <xref:System.ServiceModel.ConcurrencyMode.Single>  
  
#### <a name="contract-behaviors"></a>Sözleşme Davranışları  
 Belirli bir sözleşme için, bu arabirimdeki ve bu arabirimin ebeveynleri üzerindeki tüm sözleşme davranış öznitelikleri uygulanır. Devralma hiyerarşisinde birden çok yerde aynı tür öznitelik uygulanırsa, en çok türetilmiş tür kullanılır.  
  
#### <a name="operation-behaviors"></a>Operasyon Davranışları  
 Belirli bir işlem varolan bir soyut veya sanal işlemi geçersiz kılmazsa, devralma kuralları uygulanmaz.  
  
 Bir işlem varolan bir işlemi geçersiz kılarsa, o işlemdeki ve bu işlemin ebeveynleri üzerindeki tüm işlem davranış öznitelikleri uygulanır.  Devralma hiyerarşisinde birden çok yerde aynı tür öznitelik uygulanırsa, en çok türetilmiş tür kullanılır.
