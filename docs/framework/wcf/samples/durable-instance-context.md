---
title: "Dayanıklı Örnek Bağlamı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4f1f3f9e840ba422e327792ec2b0554fad45902
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="durable-instance-context"></a>Dayanıklı Örnek Bağlamı
Bu örnek nasıl özelleştirileceğini gösteren [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dayanıklı örnek bağlamı etkinleştirmek için çalışma zamanı. SQL Server 2005 (SQL Server 2005 Express bu durumda), yedekleme deposu olarak kullanır. Ancak, özel depolama mekanizmaları erişmek için bir yol da sağlar.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek kanal katmanını ve, hizmet modeli katmanını genişletme içerir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Bu nedenle uygulama ayrıntılarını geçmeden önce temel kavramları anlamanız gereklidir.  
  
 Dayanıklı örnek bağlamı gerçek dünya senaryolarında genellikle bulunabilir. Alışveriş sepeti uygulaması, örneğin, yarı yarıya aracılığıyla alışveriş duraklatma ve başka bir günde devam etmek için yüklemeyebilir. Biz alışveriş sepeti sonraki gün ziyaret ettiğinizde böylece bizim özgün bağlamı geri yüklendi. Biz değilken alışveriş sepeti uygulaması (sunucu) alışveriş sepeti örneği korumaz dikkate almak önemlidir. Bunun yerine, durumu sağlam bir ortamdan devam ederse ve geri yüklenen bağlamı için yeni bir örnek oluşturulurken kullanır. Bu nedenle aynı bağlam için hizmet verebilir hizmet örneği önceki örneği ile aynı değil (diğer bir deyişle, aynı bellek adresi yok).  
  
 Bir bağlam kimliği istemci ve hizmet arasındaki alış verişleri küçük bir protokolü tarafından dayanıklı örnek bağlamı mümkün hale getirilir. Bu bağlam kimliği istemcide oluşturulur ve Hizmeti'ne aktarılan. Hizmet örneği oluşturulduğunda, bu bağlam Kimliğine karşılık gelen kalıcı depolama biriminden kalıcı durum yüklemek hizmet çalışma zamanı çalışır (varsayılan olarak bu, bir SQL Server 2005 veritabanı'dir). Durum yok kullanılabiliyorsa, yeni örnek varsayılan durumuna sahiptir. Hizmet uygulaması, hizmet uygulaması durumunu değiştirin ve böylece çalışma zamanı hizmet örneği başlatma sonrasında kaydedebilirsiniz işlemleri işaretlemek için özel bir öznitelik kullanır.  
  
 Önceki Açıklama tarafından iki adımı kolayca hedefe ulaşmak için ayırt edilebilir:  
  
1.  İçerik kimliği taşımak için kablo gider ileti değiştirin  
  
2.  Özel örneklemesini mantığını uygulamak için hizmet yerel davranışını değiştirin.  
  
 Listedeki birinci kablo iletilerde etkilediğinden özel bir kanalda uygulanması gerekir ve kanal katmana sayfaya. İkinci yalnızca hizmet yerel davranışını etkiler ve bu nedenle birkaç hizmet genişletilebilirlik noktaları genişleterek uygulanabilir. Sonraki birkaç bölümlerde, bu uzantıların her ele alınmıştır.  
  
## <a name="durable-instancecontext-channel"></a>Dayanıklı InstanceContext kanal  
 İlk şey bakmak için bir kanal katman uzantısıdır. Özel bir kanalda yazma ilk adımı kanal iletişimi yapısına karar vermektir. Yeni bir kablo protokolü tanıtılan kanal neredeyse her bir kanal kanal yığınında çalışması gerekir. Bu nedenle, tüm ileti exchange desenleri desteklemelidir. Ancak, kanal çekirdek işlevselliğini communication yapısını bakılmaksızın aynı olacak. Daha açık belirtmek gerekirse istemciden bağlam Kimliğini iletileri okuma ve yazma ve hizmetinden bu bağlam Kimliğini gelen iletileri okur ve üst düzey geçirin. Nedeniyle, bir `DurableInstanceContextChannelBase` sınıfı, tüm dayanıklı örnek bağlamı kanal uygulamaları için Özet temel sınıf olarak davranan oluşturulur. Bu sınıf, genel durumu makine yönetim işlevleri ve uygulamak ve bağlam bilgilerini ve gelen iletileri okumak için iki korumalı üyeleri içerir.  
  
```  
class DurableInstanceContextChannelBase  
{  
  //…  
  protected void ApplyContext(Message message)  
  {  
    //…              
  }  
  protected string ReadContextId(Message message)  
  {  
    //…              
  }  
}  
```  
  
 Bu iki yöntem olun kullanımı `IContextManager` yazmak ve bağlam kimliği için veya iletisi okumak için uygulamaları. (`IContextManager` sözleşme tüm içerik yöneticileri için tanımlamak için kullanılan özel bir arabirim.) Kanal ya da özel bir SOAP üstbilgisi veya bir HTTP tanımlama bilgisi üstbilgisi bağlam Kimliğini içerebilir. Her bağlamı Yöneticisi uygulama devraldığı `ContextManagerBase` ortak işlevsellik için tüm içerik yöneticileri içeren sınıf. `GetContextId` Yöntemi bu sınıftaki istemciden context ID kaynaklanan için kullanılır. Kimliği ilk kez kaynaklanan bir içerik olduğunda, bu yöntem adı (tipik URI geçersiz dosya adı karakterleri karakter değiştirilir) uzak uç noktası adresi tarafından oluşturulan bir metin dosyasına kaydeder.  
  
 Daha sonra içerik kimliği aynı uzak uç nokta için gerekli olduğunda, uygun bir dosya var olup olmadığını denetler. Aşması durumunda bağlam Kimliğini okur ve döndürür. Aksi halde yeni oluşturulan bağlam Kimliğini döndürür ve bir dosyaya kaydeder. Varsayılan yapılandırma ile bu dosyalar geçerli kullanıcının temp dizininde bulunan ContextStore adlı bir dizin yerleştirilir. Ancak bu konum bağlama öğesi kullanılarak yapılandırılabilir.  
  
 İçerik kimliği taşıma için kullanılan mekanizma yapılandırılabilir. Ya da HTTP tanımlama bilgisi üstbilgisi veya özel bir SOAP üstbilgi yazılabilir. Özel SOAP üstbilgi yaklaşım HTTP olmayan protokolleri (örneğin, TCP veya Named Pipes) ile bu protokolü kullanmayı mümkün kılar. İki sınıf vardır, yani `MessageHeaderContextManager` ve `HttpCookieContextManager`, bu iki seçenek uygulayın.  
  
 Bunların her ikisi de bağlam Kimliğini iletiye uygun şekilde yazın. Örneğin, `MessageHeaderContextManager` sınıfı yazar, bir SOAP üstbilgisini `WriteContext` yöntemi.  
  
```  
public override void WriteContext(Message message)  
{  
  string contextId = this.GetContextId();  
  
  MessageHeader contextHeader =  
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,  
      DurableInstanceContextUtility.HeaderNamespace,  
      contextId,   
      true);  
  
  message.Headers.Add(contextHeader);  
}   
```  
  
 Hem `ApplyContext` ve `ReadContextId` yöntemleri `DurableInstanceContextChannelBase` sınıfı çağırma `IContextManager.ReadContext` ve `IContextManager.WriteContext`sırasıyla. Ancak, bu içerik yöneticileri doğrudan tarafından oluşturulmaz `DurableInstanceContextChannelBase` sınıfı. Bunun yerine kullanır `ContextManagerFactory` bu işlemi yapmak için sınıf.  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 `ApplyContext` Yöntemi gönderen kanalları tarafından çağrılır. Giden iletiler için bağlam kimliği yerleştirir. `ReadContextId` Yöntemi alıcı kanalları tarafından çağrılır. Bu yöntem bağlam Kimliğini gelen iletiler kullanılabilir ve ona ekler sağlar `Properties` koleksiyonu `Message` sınıfı. Ayrıca oluşturur bir `CommunicationException` bağlam Kimliğini okumak için arıza durumunda ve bu nedenle kanal durdurulmasına neden olur.  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 Devam etmeden önce kullanımını anlamak önemlidir `Properties` koleksiyonunda `Message` sınıfı. Genellikle, bu `Properties` koleksiyonu geçirme verilerini üst düzey kanal katmanından daha düşük olduğunda kullanılır. Bu şekilde istenen verilere protokol ayrıntılarını bağımsız olarak tutarlı bir şekilde üst düzey sağlanabilir. Diğer bir deyişle, kanal katmanını gönderebilir ve bağlam Kimliğini bir SOAP üstbilgi ya da bir HTTP tanımlama bilgisi üstbilgisi olarak da alabilirsiniz. Ancak bu bilgileri kanal katmanını kullanılabilir hale getirir çünkü bu ayrıntılarını bilmek üst düzey için gerekli değildir `Properties` koleksiyonu.  
  
 Şimdi ile `DurableInstanceContextChannelBase` sınıf yerinde on (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, gerekli arabirimleri IDuplexChannel, da IDuplexSessionChannel öğelerini) uygulanması gerekir. Bunlar her kullanılabilir ileti değişim deseni (veri birimi, tek yönlü, çift yönlü ve bunların süre sonuyla çeşitleri) benzer. Bu uygulamaların her biri devral çağrıları ve daha önce açıklanan temel sınıf `ApplyContext` ve `ReadContexId` uygun şekilde. Örneğin, `DurableInstanceContextOutputChannel` - IOutputChannel arabirimi uygulayan - çağırır `ApplyContext` yöntemi her yönteminden iletileri gönderir.  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 Diğer taraftan, `DurableInstanceContextInputChannel` -hangi uygular `IInputChannel` interface - çağrıları `ReadContextId` yöntemi her yönteminde iletilerini alır.  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 Bunun dışında bu kanal uygulamaları bunları aşağıda kanal kanal yığınında yöntemi çağrılarına temsilci. Ancak, süre sonuyla çeşitleri bağlam Kimliğini gönderilir ve oluşturulacak oturum neden yalnızca ilk ileti için okuma emin olmak için bir temel mantığı vardır.  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 Bu kanal uygulamaları daha sonra eklenen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal çalışma zamanı tarafından `DurableInstanceContextBindingElement` sınıfı ve `DurableInstanceContextBindingElementSection` uygun şekilde sınıfı. Bkz: [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanal bağlama öğeleri ve bağlama öğesi bölümleri hakkında daha fazla ayrıntı için örnek belgeleri.  
  
## <a name="service-model-layer-extensions"></a>Hizmet modeli katmanını uzantıları  
 İçerik kimliği kanal katmanını seyahat, hizmet davranışı örneklemesi özelleştirmek için uygulanabilir. Bu örnekte, bir Depolama Yöneticisi'ni yüklemek ve bilgisayara veya kalıcı depoya durumunu kaydetmek için kullanılır. Daha önce açıklandığı gibi bu örnek, yedekleme deposu olarak SQL Server 2005'in kullandığı Depolama Yöneticisi sağlar. Ancak, aynı zamanda bu uzantı için özel depolama mekanizmaları eklemek mümkündür. Ortak bir arabirim Bunu yapmak için tüm depolama yöneticileri tarafından uygulanmalıdır bildirildi.  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 `SqlServerStorageManager` Sınıfı içeren varsayılan `IStorageManager` uygulaması. İçinde `SaveInstance` yöntemi belirtilen nesneyi XmlSerializer kullanarak serileştirilen ve SQL Server veritabanına kaydedilir.  
  
```  
XmlSerializer serializer = new XmlSerializer(state.GetType());  
string data;  
  
using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))  
{  
    serializer.Serialize(writer, state);  
    data = writer.ToString();  
}  
  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";  
  
    using (SqlCommand command = new SqlCommand(update, connection))  
    {  
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
  
        int rows = command.ExecuteNonQuery();  
  
        if (rows == 0)  
        {  
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";  
            command.CommandText = insert;  
            command.ExecuteNonQuery();  
        }  
    }  
}  
```  
  
 İçinde `GetInstance` yöntemi serileştirilmiş verilerini okuma için belirtilen bağlamda kimliği ve ondan oluşturulan nesne çağırana döndürülür.  
  
```  
object data;  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";  
    using (SqlCommand command = new SqlCommand(select, connection))  
    {  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
        data = command.ExecuteScalar();  
    }  
}  
  
if (data != null)  
{  
    XmlSerializer serializer = new XmlSerializer(type);  
    using (StringReader reader = new StringReader((string)data))  
    {  
        object instance = serializer.Deserialize(reader);  
        return instance;  
    }  
}  
```  
  
 Kullanıcılar bu depolama yöneticileri doğrudan örneği oluşturmak için beklenen değil. Kullandıkları `StorageManagerFactory` Depolama Yöneticisi oluşturma ayrıntılarının soyutlar sınıfı. Bu sınıf bir statik, üyenin `GetStorageManager`, belirli Depolama Yöneticisi türünün bir örneği oluşturur. Tür parametresi ise `null`, bu yöntem varsayılan örneği oluşturur `SqlServerStorageManager` sınıfı ve döndürür. Ayrıca bunu uygulayan emin olmak için belirtilen tür doğrular `IStorageManager` arabirimi.  
  
```  
public static IStorageManager GetStorageManager(Type storageManagerType)  
{  
IStorageManager storageManager = null;  
  
if (storageManagerType == null)  
{  
    return new SqlServerStorageManager();  
}  
else  
{  
    object obj = Activator.CreateInstance(storageManagerType);  
  
    // Throw if the specified storage manager type does not  
    // implement IStorageManager.  
    if (obj is IStorageManager)  
    {  
        storageManager = (IStorageManager)obj;  
    }  
    else  
    {  
        throw new InvalidOperationException(  
                  ResourceHelper.GetString("ExInvalidStorageManager"));  
    }  
  
    return storageManager;  
}                  
}   
```  
  
 Okumak ve kalıcı depolama biriminden örnekleri yazmak için gerekli altyapıyı uygulanır. Şimdi hizmet davranışını değiştirmek için gerekli adımları alınması gerekir.  
  
 Bu işlem ilk adım olarak geçerli InstanceContext kanal katmanını gelen bağlam Kimliğini kaydetmek sahibiz. InstanceContext arasında bağlantı gibi davranır bir çalışma zamanı bileşeni olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dağıtıcısı ve hizmet örneği. Ek durum ve hizmet örneğine davranışı sağlamak için kullanılabilir. Süre sonuyla iletişiminde bağlam Kimliğini yalnızca ilk iletinin gönderildiği için gereklidir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Yeni durum ve Genişletilebilir nesne modeli kullanarak davranışı ekleyerek kendi InstanceContext çalışma zamanı bileşeni genişletme sağlar. Genişletilebilir object deseni kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ya da mevcut çalışma zamanı sınıflarını yeni işlevselliği ile genişletmek veya yeni durumu özellik için bir nesne eklemek için. Genişletilebilir nesne modelinde - IExtensibleObject üç arabirimi olan\<T >, IExtension\<T > ve IExtensionCollection\<T >:  
  
-   IExtensibleObject\<T > arabirimini işlevleriyle özelleştirme uzantılarına izin ver nesneler tarafından gerçekleştirilir.  
  
-   IExtension\<T > arabirimini uzantıları t türü sınıfların nesneleri tarafından uygulanan  
  
-   IExtensionCollection\<T > arabirimini türlerine göre IExtensions almak için izin veren IExtensions koleksiyonudur.  
  
 Bu nedenle bir InstanceContextExtension sınıfı IExtension arabirimini uygulayan ve bağlam kimliğini kaydetmek için gerekli durumu tanımlayan oluşturulmalıdır Bu sınıf ayrıca Depolama Yöneticisi kullanılan tutmak için durumu sağlar. Yeni durum kaydedildikten sonra bunu değiştirmek mümkün olmamalıdır. Bu nedenle durumu sağlanan ve oluşturulan ve ardından yalnızca erişilebilir salt okunur özellikler kullanarak aynı anda örneğine kaydedildi.  
  
```  
// Constructor  
public DurableInstanceContextExtension(string contextId,   
            IStorageManager storageManager)  
{  
    this.contextId = contextId;  
    this.storageManager = storageManager;              
}  
  
// Read only properties  
public string ContextId  
{  
    get { return this.contextId; }  
}  
  
public IStorageManager StorageManager  
{  
    get { return this.storageManager; }              
}   
```  
  
 InstanceContextInitializer sınıfı IInstanceContextInitializer arabirimini uygulayan ve örnek bağlamı uzantısını yapılandırılan InstanceContext uzantıları koleksiyonuna ekler.  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
    string contextId =   
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];  
  
    DurableInstanceContextExtension extension =  
                new DurableInstanceContextExtension(contextId,   
                     storageManager);  
    instanceContext.Extensions.Add(extension);  
}  
```  
  
 İçerik kimliği okuma daha önce açıklandığı gibi `Properties` koleksiyonu `Message` sınıfı ve uzantı sınıfı oluşturucuya geçirilen. Bu, tutarlı bir şekilde katmanlar arasında bilgi nasıl değiştirilebilir gösterir.  
  
 Önemli bir sonraki adım, hizmet örneği oluşturma işlemini geçersiz kılma. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Özel örneklemesi davranışları uygulama ve IInstanceProvider arabirimini kullanarak çalışma zamanı kadar takma sağlar. Yeni `InstanceProvider` sınıfı, bu işlemi yapmak için uygulanır. Oluşturucuda örneği Sağlayıcısı'ndan beklenen hizmet türünü kabul edilir. Daha sonra bu yeni örnekleri oluşturmak için kullanılır. İçinde `GetInstance` uygulama Depolama Yöneticisi örneği oluşturulur kalıcı bir örneğin aranıyor. Döndürürse `null` hizmet türü yeni bir örneğini örneği ve yapana.  
  
```  
public object GetInstance(InstanceContext instanceContext, Message message)  
{  
    object instance = null;  
  
    DurableInstanceContextExtension extension =  
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();  
  
    string contextId = extension.ContextId;  
    IStorageManager storageManager = extension.StorageManager;              
  
    instance = storageManager.GetInstance(contextId, serviceType);          
  
    if (instance == null)  
    {  
        instance = Activator.CreateInstance(serviceType);  
    }  
  
    return instance;  
}  
```  
  
 Sonraki önemli bir adım yüklemektir `InstanceContextExtension`, `InstanceContextInitializer` ve `InstanceProvider` hizmet modeli çalışma zamanı sınıflara. Özel bir öznitelik davranışı yüklemek için hizmet uygulaması sınıfları işaretlemek için kullanılabilir. `DurableInstanceContextAttribute` Bu öznitelik için uygulama içerir ve bunu uygulayan `IServiceBehavior` tüm hizmet çalışma zamanı genişletmek için arabirim.  
  
 Bu sınıf, kullanılacak Depolama Yöneticisi türü kabul eden bir özelliğe sahiptir. Bu şekilde, kendi belirtmek kullanıcıların uygulama sağlar `IStorageManager` bu öznitelik parametre olarak uygulamasıdır.  
  
 İçinde `ApplyDispatchBehavior` uygulama `InstanceContextMode` geçerli `ServiceBehavior` özniteliği doğrulanır. Bu özellik tekliye ayarlarsanız, dayanıklı depolamasına etkinleştirme mümkün değildir ve bir `InvalidOperationException` konak bildirmek için oluşturulur.  
  
```  
ServiceBehaviorAttribute serviceBehavior =  
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();  
  
if (serviceBehavior != null &&  
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)  
{  
    throw new InvalidOperationException(  
       ResourceHelper.GetString("ExSingeltonInstancingNotSupported"));  
}  
```  
  
 Bundan sonra Depolama Yöneticisi, örnek bağlamı başlatıcı ve örnek sağlayıcısı örnekleri oluşturulur ve yüklü `DispatchRuntime` için her bir uç noktası oluşturuldu.  
  
```  
IStorageManager storageManager =   
    StorageManagerFactory.GetStorageManager(storageManagerType);  
  
InstanceContextInitializer contextInitializer =  
    new InstanceContextInitializer(storageManager);  
  
InstanceProvider instanceProvider =  
    new InstanceProvider(description.ServiceType);  
  
foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
{  
    ChannelDispatcher cd = cdb as ChannelDispatcher;  
  
    if (cd != null)  
    {  
        foreach (EndpointDispatcher ed in cd.Endpoints)  
        {  
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);  
            ed.DispatchRuntime.InstanceProvider = instanceProvider;  
        }  
    }  
}  
```  
  
 Şu ana kadar Özet olarak, bu örnek özel kablo protokolü özel bağlam kimliği exchange için etkinleştirilmiş bir kanal üretilen ve aynı zamanda örnekleri kalıcı depolama biriminden yüklemek için davranış depolamasına varsayılan üzerine yazar.  
  
 Ne sol, hizmet örneği kalıcı depolama alanına kaydetmek için bir yoldur. Daha önce açıklandığı gibi zaten var. durumunda kaydetmek için gerekli işlevselliği bir `IStorageManager` uygulaması. Biz şimdi bu ile tümleştirmeniz gerekir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı. Başka bir öznitelik gerekli olan hizmet uygulaması sınıfı yöntemleri için geçerlidir. Bu öznitelik hizmet örneğinin durumunu değiştirme yöntemleri uygulanması gerekiyor.  
  
 `SaveStateAttribute` Sınıfı bu işlev uygular. Ayrıca uygulayan `IOperationBehavior` değiştirmek için sınıf [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her bir işlemin çalışma zamanı. Bir yöntem bu özniteliği ile işaretlendiğinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı çağırır `ApplyBehavior` yöntemi uygun sırasında `DispatchOperation` oluşturulmuyor. Bu yöntem uygulamasında tek satırlık bir kod yoktur:  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 Bu yönerge bir örneğini oluşturur `OperationInvoker` yazın ve atar `Invoker` özelliği `DispatchOperation` oluşturulamıyor. `OperationInvoker` İçin oluşturulan varsayılan işlemi çağırıcı için sarmalayıcı sınıftır `DispatchOperation`. Bu sınıf uygulayan `IOperationInvoker` arabirimi. İçinde `Invoke` yöntem uygulaması iç işlem çağırıcı gerçek yöntem çağırma temsilcisi. Ancak, Depolama Yöneticisi'nde sonuçları dönmeden önce `InstanceContext` hizmet örneği kaydetmek için kullanılır.  
  
```  
object result = innerOperationInvoker.Invoke(instance,  
    inputs, out outputs);  
  
// Save the instance using the storage manager saved in the   
// current InstanceContext.  
InstanceContextExtension extension =  
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();  
  
extension.StorageManager.SaveInstance(extension.ContextId, instance);  
return result;  
```  
  
## <a name="using-the-extension"></a>Uzantı kullanma  
 Kanal katman ve hizmet modeli katmanını uzantıları bitti hem de artık kullanılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar. Özel bağlama kullanma kanal yığına kanal eklemek ve uygun özniteliklere sahip hizmet uygulaması sınıfları işaretlemek hizmetler sahiptir.  
  
```  
[DurableInstanceContext]  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class ShoppingCart : IShoppingCart  
{  
//…  
     [SaveState]  
     public int AddItem(string item)  
     {  
         //…  
     }  
//…  
 }  
```  
  
 İstemci uygulamaları DurableInstanceContextChannel özel bağlama kullanma kanal yığına eklemeniz gerekir. Kanalı yapılandırma dosyasında bildirimli olarak yapılandırmak için bağlama öğesi bölümü bağlama öğesi uzantıları koleksiyona eklenmesi gerekiyor.  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 Şimdi bağlama öğesi diğer standart bağlama öğeleri gibi özel bağlama ile birlikte kullanılabilir:  
  
```xml  
<bindings>  
 <customBinding>  
   <binding name="TextOverHttp">  
     <durableInstanceContext contextType="HttpCookie"/>             
     <reliableSession />  
     <textMessageEncoding />  
     <httpTransport />  
   </binding>  
 </customBinding>  
</bindings>  
```  
  
## <a name="conclusion"></a>Sonuç  
 Bu örnek özel protokol kanal oluşturma ve etkinleştirmek için hizmet davranışını özelleştirmek nasıl oluşturulacağını gösterir.  
  
 Uzantıyı daha fazla kullanıcıları izin vererek geliştirilebilir `IStorageManager` yapılandırma bölümünü kullanarak uygulama. Hizmet koduna derlemeden yedekleme deposu değiştirmek mümkün kılar.  
  
 Ayrıca bir sınıf uygulama yararlanmaya (örneğin, `StateBag`), örneğinin durumunu saklar. Bu sınıf, durumu değiştiğinde sürdürmek için sorumludur. Kaçının kullanarak bu şekilde `SaveState` özniteliği ve kalıcı iş daha doğru bir şekilde gerçekleştirebilirsiniz (örneğin, durum kalıcı durumu gerçekte değiştirildiğinde kaydetme yerine her bir yöntemle zaman zaman `SaveState` özniteliği olarak adlandırılır).  
  
 Örneği çalıştırdığınızda, aşağıdaki çıktısı görüntülenir. İstemci alışveriş sepetine iki öğe ekler ve hizmetinden'da kendi alışveriş sepeti öğeleri listesini alır. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  Hizmet yeniden veritabanı dosyasının üzerine yazar. Birden çok örnek çalıştırmaları arasında korunur durumunu izlemek için örnek çalışmaları arasında yeniden değil emin olun.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  SQL Server 2005 veya SQL Express 2005'in bu örneği çalıştırmak için çalıştırıyor olmalıdır. SQL Server 2005 çalıştırıyorsanız, hizmetin bağlantı dizesi yapılandırmasını değiştirmeniz gerekir. Makineler arası çalıştırırken, SQL Server yalnızca sunucu makinesinde gereklidir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
## <a name="see-also"></a>Ayrıca Bkz.
