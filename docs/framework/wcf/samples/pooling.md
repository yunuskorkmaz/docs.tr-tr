---
title: Biriktirme
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 2c864bd0c1d27e9c771a1b97e756c04b107ac2b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pooling"></a>Biriktirme
Bu örnek, nesne havuzu desteklemek için Windows Communication Foundation (WCF) genişletmek gösterilmiştir. Örnek sözdizimsel olarak ve anlam olarak benzer bir öznitelik oluşturmak nasıl gösterir `ObjectPoolingAttribute` Kurumsal Hizmetler işlevselliğini özniteliği. Nesne havuzu çarpıcı artırma uygulamanın performans sağlayabilir. Ancak, doğru kullanılmıyorsa ters etkisi olabilir. Nesne havuzu kapsamlı başlatma gerektiren sık kullanılan nesnelerini yeniden yükünü azaltmanıza yardımcı olur. Havuza alınmış bir nesne üzerinde bir yöntem çağrısı bir önemli tamamlamak için gereken süre, en büyük havuz boyutu sınırına hemen sonra ancak, nesne havuzu ek istekler kuyruğa atılıyor. Bu nedenle bir zaman aşımı özel durum atma tarafından bazı nesne oluşturma isteklere hizmet başarısız olabilir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Oluşturmanın ilk adımı bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uzantısıdır genişletilebilirlik noktasını kullanmak üzere karar vermek için.  
  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terimi *dağıtıcısı* sorumlu kullanıcının hizmet üzerinde yöntem çağrılarına gelen iletileri dönüştürme ve giden bir Bu yöntemden dönüş değerleri dönüştürme için bir çalışma zamanı bileşeni başvurur İleti. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti her bitiş noktasıyla ilgili bir dağıtıcı oluşturur. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bu istemciyle ilişkili sözleşme çift yönlü sözleşme ise, istemci bir dağıtıcı kullanması gerekir.  
  
 Kanal ve uç nokta dağıtıcıları kanal sunar- ve dağıtıcı davranışını denetleyen çeşitli özellikler gösterme tarafından sözleşme genelinde genişletilebilirlik. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Özelliği de inceleme, değiştirme veya dağıtma işlemi özelleştirmek olanak sağlar. Bu örnek odaklanır <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örnekleri sağlayan bir nesneye işaret etmiyor özelliği.  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], dağıtıcı kullanarak hizmet sınıfı örneği oluşturur bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, hangi uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi. Bu arabirim üç yöntem vardır:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Bir ileti geldiğinde dağıtıcısı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi. Bu yönteme çağrıları sıklığını tarafından belirlenen <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği. Örneğin, varsa <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.InstanceContextMode.PerCall> hizmet sınıfının yeni bir örneğini, bunu ulaşan her iletiyi işlemek için oluşturulan <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> bir ileti ulaştığında çağrılır.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: İleti bağımsız değişken olduğunda çağrılır dışında bu önceki yöntemin aynıdır.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Bir hizmet örneğinin ömrü ne zaman geçti, dağıtıcı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> yöntemi. İçin olduğu gibi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yöntemi, bu yönteme çağrıları sıklığını tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.  
  
## <a name="the-object-pool"></a>Nesne havuzu  
 Özel bir <xref:System.ServiceModel.Dispatcher.IInstanceProvider> uygulamasını bir hizmet için semantiği havuzu gerekli bir nesneyi sağlar. Bu nedenle, bu örnek sahip bir `ObjectPoolingInstanceProvider` özel uyarlamasını sağlayan türü <xref:System.ServiceModel.Dispatcher.IInstanceProvider> havuzu için. Zaman `Dispatcher` çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yeni bir örneği oluşturmak yerine yöntemi, özel uygulama bellek içi havuzdaki var olan bir nesne arar. Varsa, döndürülür. Aksi takdirde, yeni bir nesne oluşturulur. Uygulamasını `GetInstance` aşağıdaki örnek kodda gösterilir.  
  
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
  
 Özel `ReleaseInstance` uygulama havuzu ve azaltır için örnek yayınlandı ekler `ActiveObjectsCount` değeri. `Dispatcher` Bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle sınıf düzeyinde üyelerine erişimi eşitlenmiş `ObjectPoolingInstanceProvider` sınıfı gereklidir.  
  
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
  
 `ReleaseInstance` Yöntemi "temizleme başlatma" özelliği sağlar. Normalde havuzu nesneler en az sayıda havuzu ömrü boyunca tutar. Ancak, yapılandırmada belirtilen en üst sınıra ulaşması havuzundaki ek nesneleri oluşturma gerektiren aşırı kullanım dönemlerini olabilir. Sonuç olarak, havuzu daha az etkin hale geldiğinde fazlalık nesnelere ek yüke haline gelebilir. Bu nedenle, `activeObjectsCount` ulaştığında sıfır, boş bir süreölçer tetikler ve temizleme döngüsü gerçekleştiren başlatılır.  
  
## <a name="adding-the-behavior"></a>Davranış ekleme  
 Dağıtıcı katman uzantıları aşağıdaki davranışları kullanarak sayfaya bağlanır:  
  
-   Hizmet davranışları. Bunlar, tüm hizmet çalışma zamanı özelleştirmesi için izin verir.  
  
-   Uç nokta davranışlar. Bunlar, hizmet uç noktaları, özellikle bir kanal ve uç nokta dağıtıcısı özelleştirmesi için izin verir.  
  
-   Sözleşme davranışlar. Bunlar için her ikisini de özelleştirilmesine imkan tanımak <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci ve hizmet sırasıyla sınıfları.  
  
 Uzantı havuzu bir nesne amacıyla hizmet davranışı oluşturulması gerekir. Hizmet davranışları uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi. Hizmet modeli özel davranışlar haberdar olmak için birkaç yolu vardır:  
  
-   Özel bir öznitelik kullanma.  
  
-   İmperatively hizmet açıklaması 's davranışları koleksiyona ekleme.  
  
-   Yapılandırma dosyası genişletme.  
  
 Bu örnek özel bir öznitelik kullanır. Zaman <xref:System.ServiceModel.ServiceHost> oluşturulan hizmetin tür tanımında kullanılan öznitelikler inceler ve kullanılabilir davranışları hizmet açıklaması 's davranışları koleksiyonuna ekler.  
  
 Arabirim <xref:System.ServiceModel.Description.IServiceBehavior> üç yöntem--içerdiği <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Yöntemi davranışı hizmete uygulanabilir emin olmak için kullanılır. Bu örnekte, uygulama hizmeti ile yapılandırılmamış sağlar <xref:System.ServiceModel.InstanceContextMode.Single>. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Yöntemi hizmetin bağlamalar yapılandırmak için kullanılır. Bu senaryoda gerekli değildir. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Hizmetin dağıtıcıları yapılandırmak için kullanılır. Bu yöntem tarafından çağrılır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zaman <xref:System.ServiceModel.ServiceHost> başlatıldığını. Aşağıdaki parametreleri, bu yönteme geçirilen:  
  
-   `Description`: Bu bağımsız değişken tüm hizmet hizmet açıklamasını sağlar. Bu hizmetin uç noktaları, sözleşmeler, bağlamaları ve diğer verileri hakkında açıklama verilerini incelemek için kullanılabilir.  
  
-   `ServiceHostBase`: Bu bağımsız değişken sağlar <xref:System.ServiceModel.ServiceHostBase> , şu anda başlatılır.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulama yeni bir örnek, `ObjectPoolingInstanceProvider` örneği ve atanan <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her bir özellik <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ServiceHostBase içinde.  
  
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
  
 Ek olarak bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulama <xref:System.EnterpriseServices.ObjectPoolingAttribute> sınıfı öznitelik bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üye sahiptir. Bu üyeleri dahil <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, ve <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, .NET Enterprise Hizmetleri tarafından sağlanan özellik kümesi havuzu nesne eşleşecek şekilde.  
  
 Davranış havuzu nesne artık eklenebilir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yeni oluşturulan özel hizmet uygulamasıyla yorumlama tarafından hizmet `ObjectPooling` özniteliği.  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>Örnek çalışıyor  
 Örnek, belirli senaryolarda nesne havuzu kullanarak kazanılan performans avantajı gösterir.  
  
 Hizmet uygulaması iki hizmet--uygulayan `WorkService` ve `ObjectPooledWorkService`. Hem Hizmetleri aynı uygulama paylaşımı--Bunlar hem pahalı başlatma gerektirir ve sonra kullanıma bir `DoWork()` görece ucuz yöntemi. Tek fark `ObjectPooledWorkService` sahip yapılandırılmış nesne havuzu:  
  
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
  
 İstemci çalıştırdığınızda, arama zaman `WorkService` 5 kez. Daha sonra arama zaman `ObjectPooledWorkService` 5 kez. Saat farkı sonra görüntülenir:  
  
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
>  İstemci bir ilk çalıştırıldığında, aynı miktarda süre hakkında olabilmesi için her iki hizmet görünür. Örneği yeniden çalıştırırsanız, görebilirsiniz `ObjectPooledWorkService` söz konusu nesne örneği havuzunda zaten mevcut olduğundan çok daha hızlı döndürür.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a>Ayrıca Bkz.
