---
title: "Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7eb8e0853adbc24deb43fc1006804d7707d9a4b8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme
Davranışları etkinleştirmek, hizmet yapılandırması veya çalışma zamanı davranışını denetlemek ve doğrulamak özel uzantıları ekleyin ve varsayılan davranışı değiştirmek [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci ve hizmet uygulamaları. Bu konu, davranış arabirimleri, bunların nasıl uygulanacağını ve bunları hizmet açıklamasında (bir hizmet uygulaması) veya uç noktası (istemci uygulamasında) programlı olarak veya bir yapılandırma dosyasında nasıl ekleneceğini açıklar. Sistem tarafından sağlanan davranışları kullanma hakkında daha fazla bilgi için bkz: [hizmet çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) ve [istemci çalışma zamanı davranışını belirtme](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Davranışlar  
 Davranış türleri hizmet veya hizmet uç noktası açıklama nesneleri eklenir (hizmet veya istemci, sırasıyla) bu nesneler tarafından kullanılmadan önce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yürüten bir çalışma zamanı oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti veya bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci. Ardından çalışma zamanı özellikleri ve Sözleşme, bağlamaları ve adresler tarafından oluşturulan çalışma zamanı değiştirme yöntemleri erişebilir çalışma zamanı oluşturma işlemi sırasında bu davranışların çağrıldığında.  
  
### <a name="behavior-methods"></a>Davranış yöntemleri  
 Tüm davranışları sahip bir `AddBindingParameters` yöntemi, bir `ApplyDispatchBehavior` yöntemi, bir `Validate` yöntemi ve bir `ApplyClientBehavior` yöntemi bir özel durum ile: çünkü <xref:System.ServiceModel.Description.IServiceBehavior> yürütülemiyor bir istemcinin, onu uygulamayan `ApplyClientBehavior`.  
  
-   Kullanmak `AddBindingParameters` değiştirmek veya özel nesneleri çalışma zamanı oluşturulduğunda, bunların kullanılması için özel bağlamalar erişebileceği bir koleksiyona eklemek için bir yöntem. Örneğin, bu kanal yapılandırıldığında, biçimini etkiler koruma gereksinimlerini belirtilen nasıl ancak olmayan kanal geliştirici tarafından bilinen.  
  
-   Kullanım `Validate` emin olmak için karşılık gelen çalışma zamanı nesne ve açıklama ağaç incelemek için yöntemi bazı ölçüt kümesine uyan.  
  
-   Kullanım `ApplyDispatchBehavior` ve `ApplyClientBehavior` açıklama incelemek için yöntemleri ağaç ve hizmet ya da istemci belirli bir kapsam için çalışma zamanı değiştirin. Ayrıca, uzantısı nesneler de ekleyebilirsiniz.  
  
    > [!NOTE]
    >  Bu yöntemler bir açıklama ağacı bulunmakla yalnızca incelemek için var. Açıklama ağaç değiştirilirse tanımlanmamış bir davranıştır.  
  
 Özellikleri, değişiklik yapabilirsiniz ve, uygulayabileceğiniz özelleştirme arabirimleri hizmet ve istemci çalışma zamanı sınıfları erişilir. Hizmet türleri <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları. İstemci türleri <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.ClientOperation> sınıfları. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci ve hizmet genelindeki çalışma zamanı özellikleri ve uzantı koleksiyonlar, sırasıyla erişmek için genişletilebilirlik giriş noktaları sınıflarıdır. Benzer şekilde, <xref:System.ServiceModel.Dispatcher.ClientOperation> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfları istemci işlemi ve hizmet işlemi çalışma zamanı özellikleri ve uzantı koleksiyonlar, sırasıyla gösterir. Şunları yapabilirsiniz, ancak, daha geniş kapsamlı çalışma zamanı nesne işlemi çalışma zamanı nesne tersi varsa erişmeniz olabilir.  
  
> [!NOTE]
>  Çalışma zamanı özellikleri ve bir istemci yürütme davranışını değiştirmek için kullanabileceğiniz uzantı türleri tartışma için bkz [genişletme istemcileri](../../../../docs/framework/wcf/extending/extending-clients.md). Çalışma zamanı özellikleri ve bir hizmet dağıtıcısı yürütme davranışını değiştirmek için kullanabileceğiniz uzantı türleri tartışma için bkz [dağıtıcıları genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
 Çoğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanıcıların değil etkileşim çalışma zamanı ile doğrudan; çekirdek modeli yapıları uç noktaları, sözleşmeler, bağlamaları, adresleri ve sınıfları veya yapılandırma dosyalarında davranışları davranışı öznitelikleri gibi programlama kullanın. Bu yapıları oluşturan *açıklama ağaç*, bir hizmetini desteklemek için bir çalışma zamanı oluşturmak için tam belirtimi olduğu veya istemci tarafından açıklama ağaç açıklanmaktadır.  
  
 Davranışlarının dört tür vardır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   Hizmet davranışları (<xref:System.ServiceModel.Description.IServiceBehavior> türleri) dahil olmak üzere tüm hizmet çalışma zamanı özelleştirmenin <xref:System.ServiceModel.ServiceHostBase>.  
  
-   Uç nokta davranışları (<xref:System.ServiceModel.Description.IEndpointBehavior> türleri) hizmet uç noktaları ve bunların ilişkili özelleştirmenin <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> nesneleri.  
  
-   Sözleşme davranışları (<xref:System.ServiceModel.Description.IContractBehavior> türleri) hem özelleştirmenin <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci ve hizmet uygulamalarında sırasıyla sınıfları.  
  
-   İşlemi davranışları (<xref:System.ServiceModel.Description.IOperationBehavior> türleri) özelleştirmesini etkinleştirmek <xref:System.ServiceModel.Dispatcher.ClientOperation> ve <xref:System.ServiceModel.Dispatcher.DispatchOperation> yeniden, istemci ve hizmet sınıfları.  
  
 Uygulama yapılandırma dosyaları kullanarak özel özniteliklerini uygulayarak veya doğrudan ekleyerek bunları uygun açıklama nesnesinde davranışları koleksiyonuna çeşitli açıklama nesnelere Bu davranışların ekleyebilirsiniz. Gerekir, ancak eklenmiş bir hizmet açıklaması veya hizmet uç noktası açıklama nesne çağrılmadan önce <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Davranış kapsamları  
 Her biri belirli bir çalışma zamanı erişim kapsamı için karşılık gelen dört davranış türü vardır.  
  
#### <a name="service-behaviors"></a>Hizmet davranışları  
 Uygulama hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior>, tüm hizmet çalışma zamanı tarafından değiştirmeniz birincil sistemdir. Hizmet davranışları bir hizmet eklemek için üç mekanizma vardır.  
  
1.  Bir öznitelik hizmet sınıfını kullanma.  Zaman bir <xref:System.ServiceModel.ServiceHost> oluşturulur, <xref:System.ServiceModel.ServiceHost> uygulama yansıma hizmet türünü özniteliklerinde kümesini bulmak için kullanır. Bu özniteliklerin herhangi birini uygulamalarıdır ise <xref:System.ServiceModel.Description.IServiceBehavior>, üzerinde davranışları koleksiyonuna eklenen <xref:System.ServiceModel.Description.ServiceDescription>. Bu çalışma zamanı hizmet yapısında katılmayı bu davranışları sağlar.  
  
2.  Program aracılığıyla davranışı üzerinde davranışları koleksiyona ekleme <xref:System.ServiceModel.Description.ServiceDescription>. Bu kod aşağıdaki satırları içeren gerçekleştirilebilir:  
  
    ```  
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3.  Özel bir uygulama <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> yapılandırma genişletir. Bu uygulama yapılandırma dosyaları hizmet davranışından kullanımını etkinleştirir.  
  
 Hizmet davranışları örnekleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dahil <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı.  
  
#### <a name="contract-behaviors"></a>Sözleşme davranışları  
 Sözleşme uygulamak davranışları <xref:System.ServiceModel.Description.IContractBehavior> arabirim, hem istemci hem de hizmet çalışma zamanı arasında bir sözleşme genişletmek için kullanılır.  
  
 Sözleşme davranışları sözleşmeye eklenmesi için iki mekanizma vardır.  İlk mekanizma sözleşme arabirimi kullanılacak özel bir öznitelik oluşturmaktır. Ne zaman bir sözleşme arabirimi geçirilir çok ya da bir <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arabirimi özniteliklerinde inceler. Tüm öznitelikleri uygulamalarıdır ise <xref:System.ServiceModel.Description.IContractBehavior>, bu üzerinde davranışları koleksiyonuna eklenen <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> bu arabirim için oluşturulmuş.  
  
 Ayrıca uygulayabilirsiniz <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> özel sözleşme davranışı öznitelikte. Bu durumda, davranışı uygulandığında aşağıdaki gibidir:  
  
 •A sözleşme arabirimi. Bu durumda, herhangi bir uç nokta içindeki bu türdeki tüm sözleşmeleri davranış uygulanır ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] değerini yoksayar <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> özelliği.  
  
 •A hizmet sınıfı. Bu durumda, yalnızca biri sözleşmedir değerini Uç noktalara davranışı uygulanır <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> özelliği.  
  
 •A geri çağırma sınıfı. Bu durumda, çift yönlü istemcinin uç noktasına davranış uygulanır ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] değerini yoksayar <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> özelliği.  
  
 Davranış davranışları koleksiyona eklemek için ikinci mekanizmasıdır bir <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Sözleşme davranışlarının örnekleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dahil <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> özniteliği. Daha fazla bilgi ve bir örnek için başvuru konusuna bakın.  
  
#### <a name="endpoint-behaviors"></a>Uç nokta davranışları  
 Uygulama uç noktası davranışları <xref:System.ServiceModel.Description.IEndpointBehavior>, olarak değiştirmeniz tüm hizmet veya belirli bir uç noktası için çalışma süresi istemci birincil sistemdir.  
  
 Bir hizmet uç noktası davranışları eklemek için iki mekanizma vardır.  
  
1.  Davranış eklemek <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> özelliği.  
  
2.  Özel bir uygulama <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> yapılandırma genişletir.  
  
 Daha fazla bilgi ve bir örnek için başvuru konusuna bakın.  
  
#### <a name="operation-behaviors"></a>İşlemi davranışları  
 Uygulama işlemi davranışları <xref:System.ServiceModel.Description.IOperationBehavior> arabirim, her işlem için hem istemci hem de hizmet çalışma zamanı genişletmek için kullanılır.  
  
 İşlem için işlem davranışları eklemek için iki mekanizma vardır. İlk mekanizma üzerindeki işlemi modeller yöntem kullanılacak özel bir öznitelik oluşturmaktır. Bir işlem eklendiğinde ya da bir <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] herhangi ekler <xref:System.ServiceModel.Description.IOperationBehavior> öznitelikleri davranışları koleksiyona <xref:System.ServiceModel.Description.OperationDescription> bu işlem için oluşturulmuş.  
  
 İkinci bir oluşturulan üzerinde davranışları koleksiyonuna doğrudan davranışı ekleyerek mekanizmasıdır <xref:System.ServiceModel.Description.OperationDescription>.  
  
 İşlemi davranışlarının örnekleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dahil <xref:System.ServiceModel.OperationBehaviorAttribute> ve <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Daha fazla bilgi ve bir örnek için başvuru konusuna bakın.  
  
### <a name="using-configuration-to-create-behaviors"></a>Davranışları oluşturmak için yapılandırma kullanma  
 Hizmet ve uç nokta ve göre kodda belirtilmesi için tasarlanan veya özniteliklerini kullanarak sözleşme davranışları can; yalnızca hizmet ve uç nokta davranışları, uygulama veya Web yapılandırma dosyaları kullanılarak yapılandırılabilir. Öznitelikleri kullanarak davranışları gösterme, eklenemez, kaldırılamaz veya çalışma zamanında değiştirilmiş derleme zamanında davranışını belirtmek geliştiricilerin sağlar. Bu genellikle her zaman bir hizmeti doğru çalışması için gerekli davranışları için uygun olan (örneğin, işlem ilgili parametreleri <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> özniteliği). Yapılandırmayı kullanarak davranışları gösterme geliştiricilerin belirtim ve bu davranışları yapılandırmasını hizmeti dağıtmak olanlar bırakın olanak tanır. Bu, isteğe bağlı bileşenler ya da hizmet veya belirli yetkilendirme yapılandırmanın bir hizmet için meta veri olup gösterilen gibi diğer dağıtım özgü yapılandırma davranışları için uygundur.  
  
> [!NOTE]
>  Machine.config yapılandırma dosyasına ekleme ve bu öğeleri kilitleme tarafından şirket uygulama ilkelerini zorlamak için yapılandırma desteği davranışları de kullanabilirsiniz. Bir açıklama ve bir örnek için bkz: [nasıl yapılır: Lock aşağı Enterprise uç noktalarını](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Yapılandırması'nı kullanarak bir davranış kullanıma sunmak için bir geliştirici, türetilmiş bir sınıf oluşturmalısınız <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> ve bu uzantı yapılandırma ile kaydedin.  
  
 Aşağıdaki örnekte gösterildiği nasıl kod bir <xref:System.ServiceModel.Description.IEndpointBehavior> uygulayan <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:  
  
```  
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
  
 Özel bir yükleme yapılandırma sistemi sırayla <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, bir uzantısı olarak kayıtlı olması gerekir. Aşağıdaki kod örneği, yukarıdaki uç noktası davranışı için yapılandırma dosyası gösterir:  
  
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
  
 Burada `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` davranışı uzantı türü ve `HostApplication` içine o sınıfın derlenmiş derleme adıdır.  
  
### <a name="evaluation-order"></a>Değerlendirme sırası  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> Ve <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> çalışma zamanı programlama modeli ve açıklama oluşturmak için sorumludur. Daha önce açıklandığı gibi davranışları, derleme işlemi hizmeti, uç nokta, sözleşme ve işlem katkıda bulunun.  
  
 <xref:System.ServiceModel.ServiceHost> Davranışları aşağıdaki sırayla uygulanır:  
  
1.  Hizmet  
  
2.  Daralma  
  
3.  Uç Noktası  
  
4.  Çalışma  
  
 İçinde herhangi bir koleksiyonu davranışı hiçbir sipariş garanti edilmez.  
  
 <xref:System.ServiceModel.ChannelFactory%601> Davranışları aşağıdaki sırayla uygulanır:  
  
1.  Daralma  
  
2.  Uç Noktası  
  
3.  Çalışma  
  
 İçinde herhangi bir koleksiyonu davranışı yeniden hiçbir sipariş garanti edilmez.  
  
### <a name="adding-behaviors-programmatically"></a>Davranışları programlı olarak ekleme  
 Özelliklerini <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> hizmetinde uygulama subsequent için değiştirilmemelidir <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> yöntemi <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Bazı üyeleriyle gibi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> özelliği ve `AddServiceEndpoint` yöntemlere <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, o noktayı değiştirilirse bir özel durum. Başkalarının, bunları değiştirmek için izin verme, ancak sonuç tanımlanmadı.  
  
 Benzer şekilde, istemci üzerinde <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> değerleri değil değiştirilmelidir çağrısından sonra <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> üzerinde <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> Özelliği bu noktayı değiştirilirse bir özel durum oluşturur, ancak diğer istemci açıklama değerler hatasız değiştirilebilir. Sonuç, ancak tanımlı değil.  
  
 Hizmet veya istemci için açıklama çağrılmadan önce değiştirmeniz önerilir olup olmadığını <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Davranışı öznitelikleri için devralma kuralları  
 Tüm dört tür davranışları özniteliklerini – hizmet davranışları ve sözleşme davranışları kullanarak doldurulabilir. Öznitelikler, yönetilen nesneleri ve üyeleri ve yönetilen nesneler üzerinde tanımlanır ve üyeleri devralma desteklemesi nedeniyle davranışı öznitelikleri devralma bağlamında nasıl tanımlamak gereklidir.  
  
 Yüksek bir düzeyde, belirli bir kapsam için (örneğin, hizmet, sözleşme veya işlem), bu kapsamı için devralma hiyerarşisindeki tüm davranışı öznitelikleri uygulanan kuralıdır. Aynı türde iki davranışı öznitelikleri varsa, yalnızca en çok türetilen tür kullanılır.  
  
#### <a name="service-behaviors"></a>Hizmet davranışları  
 Verili hizmet sınıfı için tüm hizmet davranışı öznitelikleri o sınıfı ve bu sınıfın üst uygulanır. Aynı öznitelik türünde birden çok devralma hiyerarşisi yerlerde uygulanırsa, en çok türetilen tür kullanılır.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Örneğin, önceki durumda B hizmeti ile sona eriyor bir <xref:System.ServiceModel.InstanceContextMode> , <xref:System.ServiceModel.InstanceContextMode.Single>, bir <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> modu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>ve bir <xref:System.ServiceModel.ConcurrencyMode> , <xref:System.ServiceModel.ConcurrencyMode.Single>. <xref:System.ServiceModel.ConcurrencyMode> Olan <xref:System.ServiceModel.ConcurrencyMode.Single>, çünkü <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmetinde B özniteliktir "üzerinde daha fazla türetilmiş" hizmet A. üzerinde daha  
  
#### <a name="contract-behaviors"></a>Sözleşme davranışları  
 Belirli bir sözleşme için tüm davranışı öznitelikleri üzerinde arabirim ve üzerinde üst bu arabirimin uygulanacak sözleşme. Aynı öznitelik türünde birden çok devralma hiyerarşisi yerlerde uygulanırsa, en çok türetilen tür kullanılır.  
  
#### <a name="operation-behaviors"></a>İşlemi davranışları  
 Belirli bir işlemi, varolan Özet ya da sanal işlemi kılmaz, hiçbir devralma kurallar geçerlidir.  
  
 Bir işlem var olan bir işlem, ardından tüm işlemi davranışı öznitelikleri bu işlemi ve bu işlemi üst düzey geçersiz kılarsanız uygulanır.  Aynı öznitelik türünde birden çok devralma hiyerarşisi yerlerde uygulanırsa, en çok türetilen tür kullanılır.
