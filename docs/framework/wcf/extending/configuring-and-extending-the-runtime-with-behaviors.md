---
title: Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 297a951e4678e05da73193133bd6050360b041ff
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587342"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
Davranışlar, varsayılan davranışı değiştirmek ve incelemek ve doğrulama hizmet yapılandırması veya çalışma zamanı davranışını Windows Communication Foundation (WCF) hizmet ve istemci uygulamalarında özel uzantıları eklemek etkinleştirin. Bu konu, davranış arabirimleri, bunların nasıl uygulanacağını ve bunları hizmet açıklamasında (bir hizmet uygulaması) ya da uç noktası (istemci uygulamasındaki) programlı olarak veya bir yapılandırma dosyasını nasıl ekleneceğini açıklar. Sistem tarafından sağlanan davranışları kullanma hakkında daha fazla bilgi için bkz. [hizmet çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) ve [istemci çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Davranışlar  
 Davranış türleri hizmet veya hizmet uç noktası tanımı nesneleri eklenir (hizmet veya istemci, sırasıyla) önce bu nesneleri bir WCF hizmeti veya bir WCF istemcisi yürüten bir çalışma zamanı oluşturmak için Windows Communication Foundation (WCF) tarafından kullanılır. Ardından çalışma zamanı özellikleri ve Sözleşme, bağlamalar ve adresleri tarafından oluşturulan çalışma zamanını değiştirme yöntemlerini erişebilir çalışma zamanı oluşturma işlemi sırasında bu davranışların çağrıldığında.  
  
### <a name="behavior-methods"></a>Davranış yöntemleri  
 Tüm davranışları sahip bir `AddBindingParameters` yöntemi, bir `ApplyDispatchBehavior` yöntemi, bir `Validate` yöntemi ve bir `ApplyClientBehavior` yöntemi ile bir özel durum: Çünkü <xref:System.ServiceModel.Description.IServiceBehavior> yürütülemiyor bir istemcinin, onu uygulamıyor `ApplyClientBehavior`.  
  
- Kullanma `AddBindingParameters` değiştirmek veya çalışma zamanı oluşturulduğunda, bunların kullanılması için özel bağlamalar erişebileceği bir koleksiyona özel nesneleri eklemek için yöntemi. Örneğin, bu kanal oluşturulduğuna göre biçimini etkiler koruma gereksinimlerini belirtilen nasıl ancak olmayan kanal geliştirici tarafından bilinir.  
  
- Kullanım `Validate` yöntemi emin olmak için karşılık gelen çalışma zamanı nesnesi ve açıklama ağaç incelemek için bazı ölçüt kümesine uyan.  
  
- Kullanım `ApplyDispatchBehavior` ve `ApplyClientBehavior` açıklama incelemek için yöntemleri ağaç ve çalışma zamanı hizmet veya istemcinin belirli bir kapsam için değiştirin. Genişletme nesneleri de ekleyebilirsiniz.  
  
    > [!NOTE]
    >  Bir açıklama ağacı bu yöntemleri bulunmakla yalnızca İnceleme var. Bir açıklama ağaç değiştirilirse, tanımsız bir davranıştır.  
  
 Özellikler değiştirebileceğiniz ve uygulayabileceğiniz özelleştirme arabirimleri hizmet ve istemci çalışma zamanı sınıflar erişilir. Hizmet türleri <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları. İstemci türleri <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.ClientOperation> sınıfları. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci ve hizmet genelindeki çalışma zamanı özellikleri ve uzantı koleksiyonları, sırasıyla erişmek için genişletilebilirlik noktaları sınıflardır. Benzer şekilde, <xref:System.ServiceModel.Dispatcher.ClientOperation> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları istemci işlemini ve hizmet işlemi çalışma zamanı özelliklerini ve uzantı koleksiyonlar, sırasıyla gösterir. Şunları yapabilirsiniz, ancak daha geniş kapsamlı çalışma zamanı nesne işlemi çalışma zamanı nesne veya tersine, erişim gerekli olabilir.  
  
> [!NOTE]
>  Çalışma zamanı özellikleri ve bir istemci yürütme davranışını değiştirmek için kullanabileceğiniz bir uzantı türleri bir tartışma için bkz [genişletme istemciler](../../../../docs/framework/wcf/extending/extending-clients.md). Çalışma zamanı özellikleri ve hizmet dağıtıcı yürütme davranışını değiştirmek için kullanabileceğiniz bir uzantı türleri bir tartışma için bkz [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
 WCF kullanıcıların çoğu çalışma zamanı ile doğrudan etkileşimli olarak; Bunun yerine çekirdek modeli yapıları uç noktaları, sözleşmeler, bağlamaları, adresleri ve sınıfları veya yapılandırma dosyalarında davranışları davranışı öznitelikleri gibi programlama kullanın. Bu yapılar oluşturan *açıklama ağaç*istemci tarafından açıklama ağaç açıklanan veya hizmet desteklemek için bir çalışma zamanı oluşturmak için tam belirtimi olduğu.  
  
 Wcf'de davranışları dört çeşit vardır:  
  
- Hizmet davranışları (<xref:System.ServiceModel.Description.IServiceBehavior> türleri) dahil olmak üzere tüm hizmet çalışma zamanı özelleştirmenin <xref:System.ServiceModel.ServiceHostBase>.  
  
- Uç nokta davranışları (<xref:System.ServiceModel.Description.IEndpointBehavior> türleri) hizmet uç noktaları ve bunların ilişkili özelleştirmenin <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesneleri.  
  
- Sözleşme davranışları (<xref:System.ServiceModel.Description.IContractBehavior> türleri) hem özelleştirmenin <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sırasıyla hizmet ve istemci uygulamalarında sınıfları.  
  
- İşlem davranışları (<xref:System.ServiceModel.Description.IOperationBehavior> türleri) özelleştirmesini etkinleştir <xref:System.ServiceModel.Dispatcher.ClientOperation> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> yeniden, istemci ve hizmet sınıfları.  
  
 Bu davranışların çeşitli açıklama nesneleri için uygulama yapılandırma dosyaları kullanılarak özel öznitelikleri uygulayarak veya doğrudan ekleyerek bunları uygun bir açıklama nesne üzerindeki davranışları koleksiyona ekleyebilirsiniz. Hizmet açıklaması veya hizmet uç noktası tanımı nesne çağrılmadan önce eklenen gerekir, ancak <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Davranış kapsamları  
 Her biri belirli bir çalışma zamanı erişim kapsamına karşılık gelen dört davranışı türü vardır.  
  
#### <a name="service-behaviors"></a>Hizmet davranışları  
 Uygulama hizmeti davranışları <xref:System.ServiceModel.Description.IServiceBehavior>, tüm hizmet çalışma zamanı tarafından değiştirmeniz yönelik birincil mekanizmadır. Hizmet davranışları için bir hizmet eklemek için üç mekanizma vardır.  
  
1. Öznitelik hizmet sınıfını kullanarak.  Olduğunda bir <xref:System.ServiceModel.ServiceHost> oluşturulur, <xref:System.ServiceModel.ServiceHost> uygulama, hizmet türüne öznitelik kümesi bulmak için yansıtma kullanır. Bu öznitelikleri uygulamalardır, <xref:System.ServiceModel.Description.IServiceBehavior>, davranışları koleksiyona eklendikleri <xref:System.ServiceModel.Description.ServiceDescription>. Bu, çalışma zamanı hizmet oluşturma, katılmak Bu davranış sağlar.  
  
2. Program aracılığıyla davranışı davranışları koleksiyona ekleme <xref:System.ServiceModel.Description.ServiceDescription>. Bu, aşağıdaki kod satırlarını gerçekleştirilebilir:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Özel bir uygulama <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , yapılandırma genişletir. Bu hizmet davranışını uygulama yapılandırma dosyalarından kullanımını etkinleştirir.  
  
 WCF hizmet davranışları örnekler <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı.  
  
#### <a name="contract-behaviors"></a>Sözleşme davranışları  
 Sözleşme uygulayan davranışları <xref:System.ServiceModel.Description.IContractBehavior> arabirim, hem istemci hem de hizmet çalışma zamanı arasında bir sözleşme genişletmek için kullanılır.  
  
 Sözleşme davranışları sözleşmeye eklenmesi için iki mekanizma vardır.  İlk mekanizma sözleşme arabirimi kullanılacak özel bir öznitelik oluşturmaktır. Ne zaman anlaşma arabirimi geçirilir ya bir <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601>, WCF arabirimi özniteliklerinde inceler. Herhangi bir özniteliği uygulamalardır, <xref:System.ServiceModel.Description.IContractBehavior>, bunlar üzerinde davranışları koleksiyona eklenir <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> ilgili arabirim için oluşturuldu.  
  
 Ayrıca uygulayabilirsiniz <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> özel sözleşme davranışı öznitelikte. Bu durumda, uygulandığında davranışı şu şekilde olur:  
  
 •A anlaşma arabirimi. Bu durumda, bu türdeki herhangi bir uç noktasını tüm sözleşmeler davranış uygulanır ve WCF değerini yoksayar <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> özelliği.  
  
 •A hizmet sınıfı. Bu durumda, davranışı yalnızca biri sözleşmedir değerini uç uygulanır <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> özelliği.  
  
 •A geri çağırma sınıfı. Bu durumda, çift yönlü istemci uç nokta için davranış uygulanır ve WCF değerini yoksayar <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> özelliği.  
  
 Davranış davranışları koleksiyona eklemek için ikinci mekanizmadır bir <xref:System.ServiceModel.Description.ContractDescription>.  
  
 WCF sözleşmesi davranışları örnekler <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> özniteliği. Daha fazla bilgi ve örnek için başvuru konusuna bakın.  
  
#### <a name="endpoint-behaviors"></a>Uç nokta davranışları  
 Uygulayan uç nokta davranışları <xref:System.ServiceModel.Description.IEndpointBehavior>, olarak değiştirmeniz tüm hizmet veya istemci çalışma zamanı için belirli bir uç noktaya yönelik birincil mekanizmadır.  
  
 Uç nokta davranışları için bir hizmet eklemek için iki mekanizma vardır.  
  
1. Davranışların eklenmesi <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliği.  
  
2. Özel bir uygulama <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , yapılandırma genişletir.  
  
 Daha fazla bilgi ve örnek için başvuru konusuna bakın.  
  
#### <a name="operation-behaviors"></a>İşlem davranışları  
 Uygulama işlemi davranışları <xref:System.ServiceModel.Description.IOperationBehavior> arabirim, her işlem için hem istemci hem de hizmet çalışma zamanı genişletmek için kullanılır.  
  
 İşlem için işlem davranışları eklemek için iki mekanizma vardır. İlk işlem modelleri metodunda kullanılacak özel bir öznitelik oluşturmak için mekanizmadır. Bir işlem eklendiğinde ya da bir <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory>, WCF herhangi ekler <xref:System.ServiceModel.Description.IOperationBehavior> öznitelikleri davranışları koleksiyona <xref:System.ServiceModel.Description.OperationDescription> bu işlem için oluşturulan.  
  
 İkinci mekanizmadır üzerinde oluşturulmuş bir davranış koleksiyona doğrudan davranışı ekleyerek <xref:System.ServiceModel.Description.OperationDescription>.  
  
 WCF işlemi davranışları örnekler <xref:System.ServiceModel.OperationBehaviorAttribute> ve <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Daha fazla bilgi ve örnek için başvuru konusuna bakın.  
  
### <a name="using-configuration-to-create-behaviors"></a>Davranışlar oluşturma için yapılandırma kullanma  
 Hizmet ve uç nokta ve kodda belirtilmesi göre tasarlanmış ya da özniteliklerini kullanarak sözleşme davranışları can; yalnızca hizmet ve uç nokta davranışları, uygulama veya Web yapılandırma dosyaları kullanılarak yapılandırılabilir. Davranışları kullanarak öznitelikleri gösterme eklenir, kaldırılır, veya çalışma zamanında değiştirilmiş derleme zamanında bir davranışını belirtmek geliştiricilerin sağlar. Bu genellikle, her zaman bir hizmetin doğru çalışması için gerekli olan davranışları için uygun olan (örneğin, işlem ile ilgili parametreleri için <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> özniteliği). Yapılandırmayı kullanarak davranışları gösterme, geliştiricilerin belirtimi ve bu davranışların Yapılandırma hizmeti dağıtmak olanlar bırakın olanak tanır. Bu, isteğe bağlı bileşenler veya hizmet veya belirli bir yetkilendirme yapılandırması için bir hizmet için meta verileri olup kullanıma gibi diğer dağıtım özgü yapılandırma davranışları için uygundur.  
  
> [!NOTE]
>  Machine.config yapılandırma dosyasına eklemek ve bu öğeleri kilitlemek şirket uygulama ilkelerini zorlamak için yapılandırma desteği davranışları da kullanabilirsiniz. Bir açıklama ve örnek için bkz. [nasıl yapılır: Enterprise uç noktalarını kilitleme](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Yapılandırması'nı kullanarak bir davranış kullanıma sunmak için bir geliştirici, türetilmiş bir sınıf oluşturmanız gerekir <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> ve bu uzantı yapılandırmasıyla kaydedebilirsiniz.  
  
 Aşağıdaki örnekte gösterildiği nasıl kod bir <xref:System.ServiceModel.Description.IEndpointBehavior> uygulayan <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:  
  
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
  
 Özel bir yükleme yapılandırma sistemi için sırayla <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, uzantı olarak kayıtlı olması gerekir. Aşağıdaki kod örneği, yukarıdaki uç nokta davranışı için yapılandırma dosyası gösterir:  
  
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
  
 Burada `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` davranışı uzantı türü ve `HostApplication` içine o sınıfa derlenmiş bütünleştirilmiş kodun adı.  
  
### <a name="evaluation-order"></a>Değerlendirme sırası  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> Ve <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> çalışma zamanını şuradan programlama modeli ve açıklama oluşturmak için sorumludur. Daha önce açıklandığı gibi davranışları için derleme işlemi hizmet, uç nokta, sözleşme ve işlem katkıda bulunur.  
  
 <xref:System.ServiceModel.ServiceHost> Davranışları şu sırayla uygulanır:  
  
1. Hizmet  
  
2. Sözleşme  
  
3. Uç Noktası  
  
4. Çalışma  
  
 İçinde herhangi bir koleksiyon davranışların hiçbir sırası garanti edilir.  
  
 <xref:System.ServiceModel.ChannelFactory%601> Davranışları şu sırayla uygulanır:  
  
1. Sözleşme  
  
2. Uç Noktası  
  
3. Çalışma  
  
 İçinde herhangi bir koleksiyon davranışların yeniden hiçbir sırası garanti edilir.  
  
### <a name="adding-behaviors-programmatically"></a>Davranışlar programlı olarak ekleme  
 Özelliklerini <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> hizmetinde uygulama için subsequent değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> metodunda <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Bazı üyeler ister <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> özelliği ve `AddServiceEndpoint` yöntemlerde <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, bu noktanın ilerisine değiştirdiyseniz bir özel durum. Diğerleri, bunları değiştirmek için izin verir, ancak sonuç tanımsızdır.  
  
 Benzer şekilde, istemci üzerinde <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> değerlerin değil değiştirilmelidir çağrısından sonra <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> Özelliği bu noktanın ilerisine değiştirilmiş bir özel durum oluşturur, fakat diğer istemci açıklama değerler hatasız değiştirilebilir. Ancak, sonuç tanımsızdır.  
  
 Hizmet veya istemci için açıklama çağrılmadan önce değiştirmeniz önerilir olmadığını <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Devralma kuralları davranışı öznitelikleri için  
 Tüm dört tür davranışları öznitelikleri – hizmet davranışları ve sözleşme davranışlar kullanılarak doldurulabilir. Öznitelikler, yönetilen nesneleri ve üyeleri ve yönetilen nesneleri tanımlanır ve üyeleri devralma desteklemek için davranışı öznitelikleri devralma bağlamında nasıl tanımlamak gereklidir.  
  
 Yüksek bir düzeyde, belirli bir kapsam için (örneğin, hizmet, sözleşme veya işlem), ilgili kapsam için devralma hiyerarşisindeki tüm davranışı öznitelikleri uygulanır kuralıdır. Aynı türdeki iki davranışı öznitelikleri varsa, yalnızca en çok türetilen türü kullanılır.  
  
#### <a name="service-behaviors"></a>Hizmet davranışları  
 Verili hizmet sınıfı için tüm hizmet davranışı öznitelikleri o sınıfı ve o sınıfın üst öğelerinin uygulanır. Öznitelik aynı türde birden çok devralma hiyerarşisi yerlerde uygulanırsa, en çok türetilen türü kullanılır.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Örneğin, önceki durumda B hizmeti ile sonlanır bir <xref:System.ServiceModel.InstanceContextMode> , <xref:System.ServiceModel.InstanceContextMode.Single>e <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> modunu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>ve <xref:System.ServiceModel.ConcurrencyMode> , <xref:System.ServiceModel.ConcurrencyMode.Single>. <xref:System.ServiceModel.ConcurrencyMode> Olduğu <xref:System.ServiceModel.ConcurrencyMode.Single>, çünkü <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmeti B özniteliktir "hakkında daha fazla türetilmiş" hizmet a üzerinde daha  
  
#### <a name="contract-behaviors"></a>Sözleşme davranışları  
 Verilen bir sözleşme için tüm davranışı öznitelikleri üzerinde arabirim ve üzerinde daha fazla üst o arabirimin uygulanan sözleşme. Öznitelik aynı türde birden çok devralma hiyerarşisi yerlerde uygulanırsa, en çok türetilen türü kullanılır.  
  
#### <a name="operation-behaviors"></a>İşlem davranışları  
 Belirtilen işlem mevcut soyut ya da sanal bir işlemi geçersiz kılmaz, hiçbir devralma kuralları uygulayın.  
  
 Bir işlem var olan bir işlem daha sonra bu işlemi ve bu işlemi üst öğelerinin tüm işlem davranışı öznitelikleri geçersiz kılarsanız uygulanır.  Öznitelik aynı türde birden çok devralma hiyerarşisi yerlerde uygulanırsa, en çok türetilen türü kullanılır.
