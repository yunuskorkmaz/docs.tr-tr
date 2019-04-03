---
title: Dayanıklı Örnek Bağlamı
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 9981c4293f651bce3a0abaa3e0243d0d656ff257
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841457"
---
# <a name="durable-instance-context"></a>Dayanıklı Örnek Bağlamı
Bu örnek nasıl özelleştirileceğini dayanıklı örnek bağlamı etkinleştirmek için Windows Communication Foundation (WCF) çalışma zamanı gösterir. SQL Server 2005 (SQL Server 2005 Express bu durumda), yedekleme deposu olarak kullanır. Ancak, ayrıca özel depolama mekanizmaları erişmek için bir yol sağlar.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek, kanal katmanını hem de WCF hizmet modeli katmanını genişletme içerir. Bu nedenle uygulama ayrıntılarına geçmeden önce temel kavramları anlamak gereklidir.  
  
 Dayanıklı örnek bağlamı gerçek dünya senaryolarında genellikle bulunabilir. Alışveriş sepeti uygulaması, örneğin, yarı yarıya aracılığıyla alışveriş duraklatma ve başka bir gün devam özelliğine sahiptir. Böylece biz alışveriş sepetini sonraki günün ziyaret ettiğinizde, bizim orijinal bağlamdaki geri yüklenir. Biz değilken alışveriş sepeti uygulaması (sunucu) alışveriş sepeti örneği korumaz dikkat edin önemlidir. Bunun yerine, bir kalıcı depolama ortamı durumuna devam ediyorsa ve geri yüklenen bağlamı için yeni bir örneği oluşturulurken kullanır. Bu nedenle aynı bağlamının hizmet verebilir hizmet örneği önceki örnekle aynı değil (diğer bir deyişle, aynı bellek adresi yok).  
  
 Dayanıklı örnek bağlamı yapan bir bağlam kimliği istemci ve hizmet arasında küçük bir protokolü tarafından gerçekleştirilir. Bu bağlam Kimliğini istemcide oluşturulur ve Hizmeti'ne aktarılan. Hizmet çalışma zamanı hizmet örneği oluşturulduğunda, bu bağlam Kimliğine karşılık gelen bir kalıcı depolama alanından kalıcı durum yüklemeye çalışır (varsayılan olarak bu, bir SQL Server 2005 veritabanını'dir). Yeni örnek varsayılan durumuna sahipse durumu olmadan kullanılabilir. Hizmet uygulaması, çalışma zamanı başlatma sonrasında hizmet örneği kaydedebilirsiniz hizmet uygulama durumunu değiştiren işlemleri işaretlemek için özel bir öznitelik kullanır.  
  
 Önceki açıklamaya göre iki adımı kolayca kaydetme amacına ulaşmanız için ayırt edilebilir:  
  
1.  İçerik kimliği yürütmek için kablo üzerinde giden ileti değiştirin  
  
2.  Özel örneklemesini mantığını uygulamak için hizmet yerel davranışını değiştirin.  
  
 Kablodaki iletileri listesindeki ilk öğe etkilediği için özel bir kanal uygulanması gerekir ve kanal katmana aşılayın. İkincisi yalnızca hizmet yerel davranışını etkiler ve bu nedenle birkaç hizmet genişletilebilirlik noktaları genişleterek uygulanabilir. Sonraki birkaç bölümde her biri bu uzantıları ele alınmıştır.  
  
## <a name="durable-instancecontext-channel"></a>Dayanıklı InstanceContext kanal  
 Bakmak için ilk şey, bir kanal katman uzantısıdır. Özel bir kanalda yazma ilk adımı, kanal iletişimi yapısına karar vermektir. Yeni bir kablo protokolünü tanıtılan kanal kanal yığınında neredeyse herhangi bir kanal ile çalışması gerekir. Bu nedenle, tüm ileti exchange desenleri desteklemelidir. Ancak, temel işlevlerini kanal iletişimi yapısını bağımsız olarak aynıdır. Daha açık belirtmek gerekirse istemciden gelen iletileri bağlam Kimliğini yazın ve hizmetten okunduğunu bu bağlam Kimliğini ve üst düzeylere geçirin. Nedeniyle, bir `DurableInstanceContextChannelBase` sınıfı tüm dayanıklı örnek bağlamı kanal uygulamaları için soyut temel sınıf görevi gören oluşturulur. Bu sınıf, durum makine yaygın yönetim işlevlerine ve uygulamak ve bağlam bilgisi ve gelen iletileri okumak için iki korumalı üyeleri içerir.  
  
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
  
 Bu iki yöntem olun kullanım `IContextManager` bağlam kimliği için veya iletinin okunup yazılacağını uygulamaları. (`IContextManager` tüm içerik yöneticileri için anlaşma tanımlamak için kullanılan özel bir arabirim.) Kanal ya da özel bir SOAP üst bilgi ya da bir HTTP tanımlama bilgisi üstbilgisi bağlam Kimliğini içerebilir. Her İçerik Yöneticisi uygulama devraldığı `ContextManagerBase` ortak işlevsellik için tüm içerik yöneticileri içeren sınıf. `GetContextId` Yöntemi bu sınıftaki istemciden bağlam Kimliğini kaynaklanan için kullanılır. KODU ilk kez kaynaklı bir içerik olduğunda, bu yöntem adı (tipik bir URI'leri geçersiz dosya adı karakterleri içeren karakter değiştirilir) uzak uç nokta adresine göre oluşturulmuş olan bir metin dosyasına kaydeder.  
  
 Daha sonra bağlam Kimliğini aynı uzak uç nokta için gerekli olduğunda, uygun bir dosyanın var olup olmadığını denetler. Varsa, bağlam Kimliğini okur ve döndürür. Aksi halde yeni oluşturulan bağlam Kimliğini döndürür ve bir dosyaya kaydeder. Varsayılan yapılandırma ile bu dosyalar geçerli kullanıcının temp dizininde bulunduğu ContextStore adlı bir dizin yerleştirilir. Ancak bu konuma bağlama öğesi kullanılarak yapılandırılabilir.  
  
 ID kontextu taşıma için kullanılan mekanizma yapılandırılabilir. Ya da HTTP tanımlama bilgisi üstbilgisi veya özel bir SOAP üst bilgisi için yazılabilir. Özel SOAP üstbilgi yaklaşımı, bu Protokolü HTTP olmayan protokolleri (örneğin, TCP veya Named Pipes) ile kullanmak üzere mümkün kılar. İki sınıfı vardır, yani `MessageHeaderContextManager` ve `HttpCookieContextManager`, bu iki seçenek uygulayın.  
  
 Her ikisi de bağlam Kimliğini iletiye uygun şekilde yazın. Örneğin, `MessageHeaderContextManager` sınıfı için bir SOAP üst bilgisinde, Yazar `WriteContext` yöntemi.  
  
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
  
 Hem `ApplyContext` ve `ReadContextId` yöntemleri `DurableInstanceContextChannelBase` sınıfı çağırma `IContextManager.ReadContext` ve `IContextManager.WriteContext`sırasıyla. Ancak, bu bağlam yöneticileri doğrudan tarafından oluşturulmaz `DurableInstanceContextChannelBase` sınıfı. Bunun yerine kullanır `ContextManagerFactory` , işini yapması için sınıf.  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 `ApplyContext` Yöntemi gönderen kanalları tarafından çağrılır. Bu bağlam Kimliğini giden iletileri ekler. `ReadContextId` Yöntemi alma kanalları tarafından çağrılır. Bu yöntem, bağlam Kimliğini gelen iletiler kullanılabilir ve bu gruba ekler sağlar `Properties` koleksiyonunu `Message` sınıfı. Ayrıca bir `CommunicationException` bağlam Kimliğini okumak için bir arıza durumunda ve bu nedenle kanal durdurulmasına neden olur.  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 Devam etmeden önce kullanımını anlamak önemli olan `Properties` koleksiyonda `Message` sınıfı. Genellikle bu `Properties` koleksiyonu geçirme verilerini üst düzeylere kanal katmanından daha düşük olduğunda kullanılır. Bu şekilde istenen veri protokol ayrıntılarını bağımsız olarak tutarlı bir şekilde üst düzeylere sağlanabilir. Diğer bir deyişle, kanal katmanını gönderebilir ve bağlam Kimliğini bir SOAP üst bilgisi ya da bir HTTP tanımlama bilgisi üstbilgisi olarak ya da alabilirsiniz. Kanal katmanını bu bilgi kullanılabilir hale getirir çünkü ilgili bu ayrıntıları öğrenmek üst düzey için gerekli değildir, ancak `Properties` koleksiyonu.  
  
 Artık ile `DurableInstanceContextChannelBase` sınıfı yerinde on (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel'ı, IRequestSessionChannel, IReplySessionChannel, gerekli arabirimleri IDuplexChannel, da IDuplexSessionChannel öğelerini) uygulanmalıdır. Bunlar, her kullanılabilir ileti değişim deseni (veri birimi, tek yönlü, çift yönlü ve kapatamaması türevlerini) benzer. Bu uygulamalardan her biri devral çağrıları ve daha önce açıklanan temel sınıf `ApplyContext` ve `ReadContexId` uygun şekilde. Örneğin, `DurableInstanceContextOutputChannel` - IOutputChannel arabirimi uygulayan - çağırır `ApplyContext` yöntemi her yöntemden iletileri gönderir.  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 Öte yandan, `DurableInstanceContextInputChannel` -uygulayan `IInputChannel` arabirim - çağrıları `ReadContextId` yöntemi her yönteminde iletileri alır.  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 Bu dışında bu kanal uygulamaları bunları aşağıda kanala kanal yığınındaki yöntem çağrıları temsilci. Ancak kapatamaması çeşitleri, bağlam Kimliğini gönderilir ve oluşturulacak oturum neden yalnızca ilk ileti için okuma emin olmak için bir temel mantığı vardır.  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 Bu kanal uygulamaları WCF kanalı çalışma zamanı tarafından eklenen `DurableInstanceContextBindingElement` sınıfı ve `DurableInstanceContextBindingElementSection` uygun şekilde sınıfı. Bkz: [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanal bağlama öğeleri ve öğe bölümleri bağlama hakkında daha fazla ayrıntı için örnek belgeler.  
  
## <a name="service-model-layer-extensions"></a>Hizmet modeli katman uzantıları  
 Kanal katmanını bağlam Kimliğini konuşmalar yapmıştır, hizmet davranışı oluşturmada özelleştirmek için uygulanabilir. Bu örnekte, bir Depolama Yöneticisi'ni yüklemek ve durumu kalıcı depolama ya da kaydetmek için kullanılır. Bu örnek, daha önce açıklandığı şekilde, SQL Server 2005, yedekleme deposu olarak kullanan bir Depolama Yöneticisi sağlar. Ancak, aynı zamanda bu uzantı için özel depolama mekanizmaları eklemek mümkündür. Ortak bir arabirim Bunu yapmak için tüm depolama yöneticileri tarafından uygulanmalıdır bildirilir.  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 `SqlServerStorageManager` Sınıfı içeren varsayılan `IStorageManager` uygulaması. İçinde `SaveInstance` yöntemi belirtilen nesneyi XmlSerializer kullanarak serileştirilmiş ve SQL Server veritabanına kaydedilir.  
  
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
  
 İçinde `GetInstance` yöntemi serileştirilmiş veriler için belirli bir bağlam kimliği okunur ve bundan oluşturulan nesne çağırana döndürülür.  
  
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
  
 Kullanıcılar bu depolama yöneticileri doğrudan örneklemek için beklenen değil. Kullandıkları `StorageManagerFactory` sınıfını Depolama Yöneticisi oluşturma ayrıntılarının soyutlar. Bu sınıf, bir statik üye sahip `GetStorageManager`, belirli bir Depolama Yöneticisi türün örneğini oluşturur. Tür parametresi ise `null`, bu yöntem varsayılan bir örneğini oluşturur `SqlServerStorageManager` sınıfı ve döndürür. Ayrıca bunu uygulayan emin olmak için verilen tür doğrular `IStorageManager` arabirimi.  
  
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
  
 Okumak ve kalıcı depolama alanından örnekleri yazmak için gerekli altyapıyı uygulanır. Artık bir hizmet davranışını değiştirmek için gerekli adımları alınması gerekir.  
  
 Bu işlemin ilk adımı kaydetmek için geçerli InstanceContext kanal katmanını gelen bağlam Kimliğini sahibiz. InstanceContext WCF dağıtıcı ve hizmet örneği arasındaki bağlantı olarak davranan bir çalışma zamanı bileşenidir. Ek durum ve hizmet örneği için davranış sağlamak için kullanılabilir. Kapatamaması iletişimde bağlam Kimliğini yalnızca ilk iletinin gönderildiği için bu gereklidir.  
  
 Yeni durum ve Genişletilebilir nesne desenine kullanarak davranışı ekleyerek kendi InstanceContext çalışma zamanı bileşeni genişletme WCF sağlar. Genişletilebilir nesne düzeni WCF'de ya da var olan çalışma zamanı sınıflar yeni işlevlerle genişletmek veya bir nesne için yeni durum özellikler eklemek için kullanılır. Genişletilebilir nesne deseni - IExtensibleObject üç arabirimi vardır\<T >, IExtension\<T > ve IExtensionCollection\<T >:  
  
-   IExtensibleObject\<T > arabirimini işlevleriyle özelleştirme uzantılara izin ver nesneler tarafından gerçekleştirilir.  
  
-   IExtension\<T > arabirimini uzantıları t türü sınıfların nesneleri tarafından uygulanan  
  
-   IExtensionCollection\<T > türüne göre IExtensions almak için izin veren IExtensions koleksiyonunu arabirimidir.  
  
 Bu nedenle InstanceContextExtension sınıfı IExtension arabirimi uygulayan ve bağlam kimliğini kaydetmek için gerekli durumu tanımlayan oluşturulmalıdır Bu sınıf, durum Yöneticisi tarafından kullanılan depolama tutmak için de sağlar. Yeni durumu kaydedildikten sonra değiştirmek olası olmamalıdır. Bu nedenle durum sağlanan ve oluşturulan ve ardından yalnızca erişilebilir salt okunur özelliklerini kullanarak zaman örneğine kaydedilir.  
  
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
  
 InstanceContextInitializer sınıfı IInstanceContextInitializer arabirimi uygulayan ve örnek bağlamı uzantısını yapılandırılmakta InstanceContext uzantıları koleksiyonuna ekler.  
  
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
  
 Daha önce açıklandığı gibi bağlam Kimliğini gelen okunur `Properties` koleksiyonunu `Message` sınıfı ve extension sınıfının oluşturucusuna geçirilen. Bu bilgi tutarlı bir şekilde katmanlar arasında nasıl değiştirilebilir gösterir.  
  
 Önemli bir sonraki adım, hizmet örneği oluşturma işlemi geçersiz kılıyor. WCF özel oluşturmada davranışları uygulama ve bunları IInstanceProvider arabirimini kullanarak çalışma zamanı kadar takma sağlar. Yeni `InstanceProvider` sınıfı, işi yapmak için uygulanır. Oluşturucuda örneği sağlayıcısından beklenen hizmet türünü kabul edilir. Daha sonra bu yeni örnekleri oluşturmak için kullanılır. İçinde `GetInstance` uygulama Depolama Yöneticisi örneği oluşturulur için kalıcı bir örneği aranıyor. Döndürürse `null` hizmet türü yeni bir örneğini örneği ve arayana döndürülür.  
  
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
  
 Sonraki önemli adım `InstanceContextExtension`, `InstanceContextInitializer` ve `InstanceProvider` sınıflara service model çalışma zamanı. Özel bir öznitelik, hizmet uygulaması sınıflar yükleme davranışı işaretlemek için kullanılabilir. `DurableInstanceContextAttribute` Bu öznitelik için ise uygulamayı içerir ve bunu uygulayan `IServiceBehavior` tüm hizmet çalışma zamanı genişletmek için arabirim.  
  
 Bu sınıf, kullanılacak Depolama Yöneticisi türü kabul eden bir özelliğe sahiptir. Bu şekilde, uygulama kendi belirtmek kullanıcıların sağlar. `IStorageManager` bu öznitelik parametre olarak uygulamasıdır.  
  
 İçinde `ApplyDispatchBehavior` uygulama `InstanceContextMode` geçerli `ServiceBehavior` öznitelik doğrulanır. Bu özellik için Singleton olarak ayarlanırsa dayanıklı örneği oluşturmayı etkinleştirmek mümkün değildir ve bir `InvalidOperationException` ana bilgisayara bildirmek için oluşturulur.  
  
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
  
 Şu ana kadar Özet olarak, bu örnek için özel bir bağlam kimliği exchange özel kablo protokolünü etkinleştirilmiş bir kanal üretmiştir ve de varsayılan davranışı, kalıcı depolamadan örnekleri yüklenemedi depolamasına üzerine yazılır.  
  
 Ne bırakılır, hizmet örneği kalıcı depolama alanına kaydetmek için bir yoldur. Daha önce açıklandığı gibi zaten var. durumunda kaydetmek için gerekli işlevselliği bir `IStorageManager` uygulaması. Biz artık bu WCF çalışma zamanı ile tümleştirmeniz gerekir. Başka bir özniteliği gereklidir hizmet uygulaması sınıfı yöntemleri için geçerli olan. Bu öznitelik hizmet örneğinin durumunu değiştiren yöntemlere uygulanması gerekiyor.  
  
 `SaveStateAttribute` Sınıfı bu işlevselliğini uygular. Ayrıca uygulayan `IOperationBehavior` her işlem için WCF çalışma zamanını değiştirmek için sınıf. Bu özniteliği ile işaretli bir yöntem, WCF çalıştırma zamanı çağırır `ApplyBehavior` yöntemi sırasında uygun `DispatchOperation` oluşturulmuyor. Bu yöntem uygulaması tek satırlık bir kod vardır:  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 Bu yönerge bir örneğini oluşturur `OperationInvoker` yazın ve buna atayan `Invoker` özelliği `DispatchOperation` oluşturuluyor. `OperationInvoker` İçin oluşturulan varsayılan işlem çağırıcı için bir sarmalayıcı sınıftır `DispatchOperation`. Bu sınıfın uyguladığı `IOperationInvoker` arabirimi. İçinde `Invoke` gerçek yöntem çağırma için iç işlem çağırıcı temsilci yöntem uygulaması. Ancak, Depolama Yöneticisi'nde sonuçları döndüren önce `InstanceContext` hizmet örneği kaydetmek için kullanılır.  
  
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
  
## <a name="using-the-extension"></a>Uzantısını kullanma  
 Kanal katmanını ve hizmet modeli katman uzantıları bitti hem de WCF uygulamaları artık kullanılabilir. Özel bağlama kullanma kanal yığına kanal ekleyin ve ardından uygun özniteliklere sahip hizmet uygulama sınıfları işaretlemek hizmetleriniz var.  
  
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
  
 İstemci uygulamaları DurableInstanceContextChannel özel bağlama kullanma kanal yığına eklemeniz gerekir. Kanal yapılandırma dosyasında bildirimli olarak yapılandırmak için bağlama öğesi uzantıları koleksiyona eklenecek bağlama öğesi bölümü vardır.  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 Artık bağlama öğesi, diğer standart bağlama öğeleri gibi özel bir bağlama ile kullanılabilir:  
  
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
 Bu örnek bir özel Protokolü kanalının nasıl oluşturulacağı ve etkinleştirmek için hizmet davranışını özelleştirmek nasıl oluşturulacağını gösterir.  
  
 Uzantı belirtin kullanıcılar izin vererek daha fazla geliştirilebilir `IStorageManager` bir yapılandırma bölümünü kullanarak uygulama. Hizmet kodu yeniden derlemeden yedekleme deposu değiştirmek mümkün kılar.  
  
 Ayrıca bir sınıf uygulamak çalışabilir (örneğin, `StateBag`), örneğinin durumunu saklar. Bu sınıf, durumu değiştiğinde kalıcı hale getirmekten sorumludur. Kullanarak önlemek bu şekilde `SaveState` özniteliği ve kalıcı hale getirme iş daha doğru bir şekilde gerçekleştirin (örneğin, durum kalıcı durum gerçekten değiştirildiğinde kaydetmek yerine her bir yöntemle zaman zaman `SaveState` özniteliği olarak adlandırılır).  
  
 Aşağıdaki çıktı örneği çalıştırdığınızda görüntülenir. İstemci, iki öğe, alışveriş sepetine ekler ve hizmetten'da, alışveriş sepetine içinde öğelerin listesini alır. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  Hizmet yeniden oluşturma, veritabanı dosyasının üzerine yazar. Örnek birden fazla çalıştırma sonucunda korunur durumu gözlemek için örnek çalıştırma arasında yeniden emin olun.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Bu örneği çalıştırmak için SQL Server 2005 veya SQL Express 2005 çalıştırıyor olmalısınız. SQL Server 2005 çalıştırıyorsanız, hizmetin bağlantı dizesi yapılandırmasını değiştirmeniz gerekir. Çapraz makine çalıştırırken, SQL Server yalnızca sunucu makinesinde gereklidir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
