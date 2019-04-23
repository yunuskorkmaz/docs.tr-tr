---
title: Biriktirme
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: f4df661ad5d831158da55fe3890805ccc5cd695f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307216"
---
# <a name="pooling"></a>Biriktirme
Bu örnek nasıl genişleteceğinizi nesne havuzu desteklemek için Windows Communication Foundation (WCF) gösterir. Örnek sözdizimi ve anlamsal olarak benzer bir öznitelik oluşturmak nasıl gösterir `ObjectPoolingAttribute` Enterprise Hizmetleri işlevselliğinin özniteliği. Nesne havuzu bir uygulamanın performansı çarpıcı bir boost sağlayabilir. Ancak, düzgün bir şekilde kullanılmıyorsa karşı etkili sahip olabilir. Nesne havuzu kapsamlı başlatma gerektiren sık kullanılan nesnelerin yeniden yükünü azaltmanıza yardımcı olur. Havuza alınmış bir nesne üzerinde bir yönteme bir çağrı önemli miktarda zaman alıyorsa, maksimum havuz boyutuna ulaştı hemen sonra ancak nesne havuzu ek istekler kuyruğa alır. Bu nedenle bazı nesne oluşturma isteklerinin bir zaman aşımı özel durum tarafından hizmet başarısız olabilir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 WCF uzantısı oluşturmanın ilk adımı, kullanılacak genişletilebilirlik noktası karar vermektir.  
  
 Wcf'de terimi *dağıtıcı* sorumlu kullanıcının hizmeti yöntem çağrılarına gelen iletileri dönüştürme ve dönüş değerleri Bu yöntemden giden bir iletiye dönüştürmek için bir çalışma zamanı bileşeni ifade eder. Bir WCF hizmeti bir dağıtıcı için her uç nokta oluşturur. Bu istemciyle ilişkili sözleşme çift yönlü sözleşme ise bir WCF istemcisi bir dağıtıcı kullanmanız gerekir.  
  
 Kanal ve uç nokta dağıtıcıları kanal teklif- ve dağıtıcı davranışını denetleyen çeşitli özellikleri kullanıma sunan tarafından sözleşme kapsamında genişletilebilirlik. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Özelliği de incelemek, değiştirme veya özelleştirme dağıtma işlemi olanak sağlar. Bu örnek odaklanır <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örnekleri sağlayan bir nesneye işaret etmiyor özelliği.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 WCF'de, dağıtıcı hizmeti kullanarak sınıf örneği oluşturur. bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi. Bu arabirim üç yöntem vardır:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Bir ileti dağıtıcısı çağrıları geldiğinde <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi. Bu yöntem çağrıları sıklığını belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği. Örneğin, varsa <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği <xref:System.ServiceModel.InstanceContextMode.PerCall> ulaşan, bunu her iletiyi işlemek için hizmet sınıfının yeni bir örneğini oluşturan <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> bir ileti geldiğinde çağrılır.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Hiçbir ileti bağımsız değişken olduğunda çağrılır ancak bu önceki yöntemin aynıdır.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Bir hizmet örneğinin ömrünü zaman geçti, dağıtıcı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> yöntemi. İçin olduğu gibi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yöntemi, bu yöntem çağrıları sıklığına göre belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.  
  
## <a name="the-object-pool"></a>Nesne havuzu  
 Özel bir <xref:System.ServiceModel.Dispatcher.IInstanceProvider> uygulamasını bir hizmet için semantiği havuzu gerekli bir nesneyi sağlar. Bu nedenle, bu örnek sahip bir `ObjectPoolingInstanceProvider` özel uygulanışı sağlayan tür <xref:System.ServiceModel.Dispatcher.IInstanceProvider> havuzu için. Zaman `Dispatcher` çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yöntemi, yeni bir örneğini oluşturmak yerine, özel uygulama var olan bir nesne, bellek havuzunda arar. Varsa, döndürülür. Aksi takdirde, yeni bir nesne oluşturulur. Uygulamasını `GetInstance` aşağıdaki örnek kodda gösterilmiştir.  
  
```  
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
  
 Özel `ReleaseInstance` uygulama havuzu ve azaltır için yayımlanan örneği ekler `ActiveObjectsCount` değeri. `Dispatcher` Farklı iş parçacıklarından bu yöntemleri çağırabilir ve bu nedenle sınıf düzeyinde üyelerine erişim eşitlenmiş `ObjectPoolingInstanceProvider` sınıfı gereklidir.  
  
```  
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
  
 `ReleaseInstance` Yöntemi "temizleme başlatma" özelliği sağlar. Normalde havuza havuz ömrü boyunca nesnelerin en az sayıda tutar. Bununla birlikte, yapılandırmada belirtilen üst sınırına ulaşmadığınız havuzunda ek nesneleri oluşturma gerektiren aşırı kullanım dönemlerini olabilir. Sonuç olarak, havuzu daha az etkin hale geldiğinde, fazlalık nesneleri bir ek yükü olabilir. Bu nedenle, `activeObjectsCount` sıfıra indiğinde, tetikler ve bir temizleme döngüsü gerçekleştiren boş bir süreölçer başlatılır.  
  
## <a name="adding-the-behavior"></a>Davranış ekleme  
 Dağıtıcı katman uzantıları aşağıdaki davranışları kullanarak sayfaya bağlanır:  
  
-   Hizmet davranışları. Bunlar, tüm hizmet çalışma zamanı özelleştirme için izin verir.  
  
-   Uç nokta davranışları. Bu hizmet uç noktaları, özellikle bir kanal ve uç nokta dağıtıcı özelleştirme yapma olanağı sağlar.  
  
-   Sözleşme davranışlar. Bu ikisinin özelleştirme için izin <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemciyi ve hizmeti üzerinde sırasıyla sınıfları.  
  
 Uzantı havuzu bir nesne için bir hizmet davranışını oluşturulması gerekir. Hizmet davranışları uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi. Hizmet modeli özel davranışlar haberdar olmak için birkaç yol vardır:  
  
-   Özel bir öznitelik kullanma.  
  
-   Kesin hizmet açıklaması'nın davranışları koleksiyonunuza ekleniyor.  
  
-   Yapılandırma dosyası genişletme.  
  
 Bu örnek bir özel öznitelik kullanır. Zaman <xref:System.ServiceModel.ServiceHost> oluşturulur bu hizmetin türü tanımında kullanılan öznitelikler inceler ve kullanılabilir davranışlar hizmet açıklaması'nın davranışları koleksiyonuna ekler.  
  
 Arabirim <xref:System.ServiceModel.Description.IServiceBehavior> üç yöntem--içerdiğinden <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Yöntemi davranış hizmetine uygulanabilir emin olmak için kullanılır. Bu örnekte, uygulama hizmeti ile yapılandırılmamış sağlar <xref:System.ServiceModel.InstanceContextMode.Single>. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Yöntemi, hizmet bağlamalarını yapılandırmak için kullanılır. Bu senaryoda gerekli değildir. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Hizmetin dağıtıcıları yapılandırmak için kullanılır. Bu yöntem, WCF tarafından çağrılır, <xref:System.ServiceModel.ServiceHost> Başlatılmakta olan. Aşağıdaki parametreleri, bu yönteme geçirilir:  
  
-   `Description`: Bu bağımsız değişken tüm hizmet hizmet açıklamasını sağlar. Bu hizmet uç noktaları, sözleşmeler, bağlamalar ve diğer verileri hakkında açıklama verilerini incelemek için kullanılabilir.  
  
-   `ServiceHostBase`: Bu bağımsız değişken sağlar <xref:System.ServiceModel.ServiceHostBase> başlatılan şu anda.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulama yeni bir örneği, `ObjectPoolingInstanceProvider` örneği ve atanan <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her bir özellik <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ServiceHostBase içinde.  
  
```  
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
                if (throttle == null)  
                {  
                    throttle = cd.ServiceThrottle;  
                }  
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
  
 Ek olarak bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulama <xref:System.EnterpriseServices.ObjectPoolingAttribute> sınıfı özniteliği bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üyelere sahiptir. Bu üyeleri içeren <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, ve <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, .NET Enterprise Hizmetleri tarafından sağlanan havuzu nesne eşleştirilecek.  
  
 Davranış havuzu nesnesi artık bir WCF hizmeti için yeni oluşturulan özel hizmet uygulamasıyla açıklamalar eklenebilir `ObjectPooling` özniteliği.  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Örnek, belirli senaryolarda nesne havuzu kullanarak kazanılan performans avantajlarının gösterir.  
  
 İki Hizmetleri hizmet uygulamasının uygulayan `WorkService` ve `ObjectPooledWorkService`. Hem Hizmetleri aynı uygulama paylaşımı--Bunlar hem pahalı başlatma gerektirir ve sunarsınız bir `DoWork()` oldukça fazla alan kaplamıyor yöntemi. Tek fark `ObjectPooledWorkService` sahip yapılandırılmış nesne havuzu:  
  
```  
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
  
 İstemci çalıştırdığınızda, arama zaman `WorkService` 5 kez. Ardından arama zaman `ObjectPooledWorkService` 5 kez. Saat farkı ardından görüntülenir:  
  
```  
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
>  İstemci ilk çalıştırıldığında her iki hizmet de aynı süre hakkında yararlanmak için görünür. Örnek yeniden çalıştırırsanız, gördüğünüz gibi `ObjectPooledWorkService` havuzunda o nesnenin bir örneği zaten varolduğundan çok daha hızlı döndürür.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
