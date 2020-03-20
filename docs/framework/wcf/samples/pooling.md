---
title: Biriktirme
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183399"
---
# <a name="pooling"></a>Biriktirme
Bu örnek, windows communication foundation'ın (WCF) nesne havuzuna nasıl genişletileni gösterir. Örnek, Kurumsal Hizmetler'in öznitelik işlevine `ObjectPoolingAttribute` sözdizimsel ve anlamsal olarak benzeyen bir öznitelik nasıl oluşturulacak larını gösterir. Nesne birleştirme, uygulamanın performansına önemli bir destek sağlayabilir. Ancak, düzgün kullanılmaz ise ters etkiye sahip olabilir. Nesne birleştirme, yaygın başlatma gerektiren sık kullanılan nesneleri yeniden oluşturma ek yükü azaltmaya yardımcı olur. Ancak, birleştirilmiş nesne üzerindeki bir yönteme yapılan çağrının tamamlanması önemli miktarda zaman alıyorsa, nesne biriktirme kuyruğa en kısa sürede en kısa sürede en kısa sürede ek istekler bir araya getirmek. Bu nedenle, zaman adabı atarak bazı nesne oluşturma isteklerine hizmet etmeyebilir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 WCF uzantısı oluşturmanın ilk adımı, kullanılacak genişletilebilirlik noktasına karar vermektir.  
  
 WCF'de *sevkiyat* terimi, gelen iletileri kullanıcının hizmetindeki yöntem çağrılarına dönüştürmekten ve bu yöntemden giden iletiye dönüş değerlerini dönüştürmekten sorumlu bir çalışma zamanı bileşenianlamına gelir. WCF hizmeti, her bitiş noktası için bir sevk irsaliyesi oluşturur. Bir WCF istemcisi, söz konusu istemciyle ilişkili sözleşme çift yönlü bir sözleşmeyse, bir gönderici kullanmalıdır.  
  
 Kanal ve uç nokta dağıtıcıları, gönderenin davranışını kontrol eden çeşitli özellikleri açığa çıkararak kanal ve sözleşme genelinde genişletilebilirlik sunar. Özellik <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> ayrıca gönderme işlemini incelemenize, değiştirmenize veya özelleştirmenize olanak tanır. Bu örnek, hizmet <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> sınıfının örneklerini sağlayan nesneyi işaret eden özelliğe odaklanır.  
  
## <a name="the-iinstanceprovider"></a>IInstanceSağlayıcı  
 WCF'de, gönderici <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi uygulayan bir , kullanarak hizmet sınıfının örneklerini oluşturur. Bu arabirimin üç yöntemi vardır:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Bir ileti geldiğinde, Dispatcher, iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yöntemi çağırır. Bu yönteme yapılan çağrıların <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> sıklığı özellik tarafından belirlenir. Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özellik gelen her <xref:System.ServiceModel.InstanceContextMode.PerCall> iletiyi işlemek için yeni bir hizmet sınıfı <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> örneği olarak ayarlanmışsa, ileti geldiğinde çağrılır.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: İleti bağımsız değişkeni olmadığında bu çağrılan dışında, bu önceki yöntemle aynıdır.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Bir hizmet örneğinin ömrü geçtiğinde, Sevk irsaliyesi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> yöntemi çağırır. Yöntemde <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> olduğu gibi, bu yönteme yapılan çağrıların <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> sıklığı özellik tarafından belirlenir.  
  
## <a name="the-object-pool"></a>Nesne Havuzu  
 Özel <xref:System.ServiceModel.Dispatcher.IInstanceProvider> bir uygulama, bir hizmet için gerekli nesne birleştirme semantik sağlar. Bu nedenle, bu `ObjectPoolingInstanceProvider` örnek havuzlama <xref:System.ServiceModel.Dispatcher.IInstanceProvider> için özel uygulama sağlayan bir türü vardır. <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> Yöntem `Dispatcher` çağırDığında, yeni bir örnek oluşturmak yerine, özel uygulama bellek içi bir havuzda varolan bir nesneyi arar. Varsa, döndürülür. Aksi takdirde, yeni bir nesne oluşturulur. `GetInstance` Uygulama aşağıdaki örnek kodda gösterilir.  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;
}  
```  
  
 Özel `ReleaseInstance` uygulama, serbest bırakılan örneği havuza geri ekler `ActiveObjectsCount` ve değeri eriter. Bu `Dispatcher` yöntemleri farklı iş parçacıklarından arayabilirsiniz ve bu nedenle `ObjectPoolingInstanceProvider` sınıftaki sınıf düzeyi üyelerine eşitlenmiş erişim gereklidir.  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();
    }  
}  
```  
  
 Yöntem `ReleaseInstance` bir "önbaşlatma temizleme" özelliği sağlar. Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar. Ancak, yapılandırmada belirtilen maksimum sınıra ulaşmak için havuzda ek nesneler oluşturmayı gerektiren aşırı kullanım dönemleri olabilir. Sonunda, havuz daha az etkin hale geldiğinde, bu artı nesneler ek bir ek yükü haline gelebilir. Bu nedenle, `activeObjectsCount` sıfıra ulaştığında, bir temizleme döngüsünü tetikleyen ve gerçekleştiren bir boşta zamanlayıcı başlatılır.  
  
## <a name="adding-the-behavior"></a>Davranışı Ekleme  
 Dispatcher katmanı uzantıları aşağıdaki davranışları kullanarak bağlanır:  
  
- Hizmet Davranışları. Bunlar, tüm hizmet çalışma zamanının özelleştirilmesine olanak sağlar.  
  
- Bitiş Noktası Davranışları. Bunlar, hizmet bitiş noktalarının, özellikle bir Kanal ve Bitiş Noktası Göndericinin özelleştirilmesine olanak sağlar.  
  
- Sözleşme Davranışları. Bunlar, istemci ve <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> hizmet sırasıyla hem de sınıfların özelleştirilmesiiçin izin verir.  
  
 Bir nesne birleştirme uzantısı amacıyla bir hizmet davranışı oluşturulmalıdır. Hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulanarak oluşturulur. Hizmet modelini özel davranışlardan haberdar etmenin birkaç yolu vardır:  
  
- Özel bir öznitelik kullanma.  
  
- Zorunlu olarak hizmet açıklamasının davranış koleksiyonuna ekleme.  
  
- Yapılandırma dosyasını genişletme.  
  
 Bu örnek özel bir öznitelik kullanır. <xref:System.ServiceModel.ServiceHost> Oluşturulduğunda, hizmetin tür tanımında kullanılan öznitelikleri inceler ve hizmet açıklamasının davranış koleksiyonuna kullanılabilir davranışları ekler.  
  
 Arayüzün <xref:System.ServiceModel.Description.IServiceBehavior> içinde üç yöntem <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>var <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>-- , , ve. Yöntem, <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> davranışın hizmete uygulanabilmesini sağlamak için kullanılır. Bu örnekte, uygulama hizmetin <xref:System.ServiceModel.InstanceContextMode.Single>. Yöntem, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> hizmetin bağlaçlarını yapılandırmak için kullanılır. Bu senaryoda gerekli değildir. Bu, <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> hizmetin sevk gönderimlerini yapılandırmak için kullanılır. Bu yöntem, başharflere <xref:System.ServiceModel.ServiceHost> para verilirken WCF tarafından çağrılır. Aşağıdaki parametreler bu yönteme aktarılır:  
  
- `Description`: Bu bağımsız değişken, tüm hizmet için hizmet açıklamasını sağlar. Bu, hizmetin uç noktaları, sözleşmeleri, ciltleri ve diğer verilerle ilgili açıklama verilerini incelemek için kullanılabilir.  
  
- `ServiceHostBase`: Bu bağımsız <xref:System.ServiceModel.ServiceHostBase> değişken, şu anda başharflere getirilmekte olan şeyi sağlar.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamada yeni bir `ObjectPoolingInstanceProvider` örnek anında ve ServiceHostBase <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her <xref:System.ServiceModel.Dispatcher.DispatchRuntime> özelliğine atanır.  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior
    // (this.throttlingBehavior==null), it should have initialized
    // a single ServiceThrottle on all ChannelDispatchers.
    // As we loop through the ChannelDispatchers, we verify that
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all
            // endpoints. If there were others, we could not enforce
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 Bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulamaya ek <xref:System.EnterpriseServices.ObjectPoolingAttribute> olarak sınıf öznitelik bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üye vardır. Bu <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>üyeler, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>.NET Enterprise Services tarafından sağlanan nesne birleştirme özelliğini eşleştirmek için , ve <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, içerir.  
  
 Nesne birleştirme davranışı artık yeni oluşturulan özel `ObjectPooling` öznitelik ile hizmet uygulaması açıklama yaparak bir WCF hizmetine eklenebilir.  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Örneği Çalıştırma  
 Örnek, belirli senaryolarda nesne havuzu kullanılarak elde edilebilen performans avantajlarını gösterir.  
  
 Hizmet uygulaması iki hizmet `WorkService` uygular `ObjectPooledWorkService`-- ve . Her iki hizmet de aynı uygulamayı paylaşıyor - her `DoWork()` ikisi de pahalı bir başlangıç gerektiriyor ve sonra nispeten ucuz bir yöntemi ortaya çıkarıyor. Tek fark, yapılandırılan nesne havuzu `ObjectPooledWorkService` olmasıdır:  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }
}  
```  
  
 İstemciyi çalıştırdığınızda, `WorkService` 5 kez arama zaman. Daha sonra kez `ObjectPooledWorkService` 5 kez arama. Zaman farkı daha sonra görüntülenir:  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> İstemci ilk kez çalıştırıldığı zaman, her iki hizmet de yaklaşık olarak aynı süreyi alır gibi görünür. Örneği yeniden çalıştıran bu nesnenin bir `ObjectPooledWorkService` örneği havuzda zaten var olduğundan, çok daha hızlı döndürür görebilirsiniz.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!NOTE]
> Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
