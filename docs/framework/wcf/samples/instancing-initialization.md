---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ec44276d56b0a914c742a5a709f2207f8111e57b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827919"
---
# <a name="instancing-initialization"></a>Başlatmayı Örneklendirme
Bu örnek genişletir [toplama](../../../../docs/framework/wcf/samples/pooling.md) örnek bir arabirim tanımlayarak `IObjectControl`, etkinleştirme ve devre dışı bırakmadan başlatma bir nesnenin özelleştirir. İstemci, nesne havuza geri dönün ve olan nesne havuza döndürmeyen yöntemleri çağırır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
## <a name="extensibility-points"></a>Genişletilebilirlik noktaları  
 Bir Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, kullanılacak genişletilebilirlik noktası karar vermektir. Wcf'de, terim *EndpointDispatcher* sorumlu kullanıcının hizmeti yöntem çağrılarına gelen iletileri dönüştürme ve dönüş değerleri Bu yöntemden giden bir iletiye dönüştürmek için bir çalışma zamanı bileşeni başvurur . Bir WCF hizmeti her uç nokta için bir EndpointDispatcher oluşturur.  
  
 Uç nokta kapsamı (hizmet tarafından gönderilen veya alınan tüm iletiler için) genişletilebilirliği kullanarak EndpointDispatcher sunar <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> sınıfı. Bu sınıf EndpointDispatcher davranışını denetleyen çeşitli özelliklerini özelleştirmenize olanak sağlar. Bu örnek odaklanır <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örnekleri sağlayan bir nesneye işaret etmiyor özelliği.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 WCF'de, EndpointDispatcher uygulayan bir örnek sağlayıcısı kullanılarak bir hizmet sınıfı örneklerini oluşturur <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi. Bu arabirim, yalnızca iki yöntem vardır:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Bir ileti geldiğinde, dağıtıcı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi. Bu yöntem çağrıları sıklığını belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği. Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, hizmet sınıfının yeni bir örneğini, bunu ulaşan her iletiyi işlemek için oluşturulan <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> bir ileti geldiğinde çağrılır.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği, iletiyi işlemeyi tamamladıktan sonra EndpointDispatcher çağırır <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi. Olarak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi, bu yöntem çağrıları sıklığına göre belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.  
  
## <a name="the-object-pool"></a>Nesne havuzu  
 `ObjectPoolInstanceProvider` Sınıfı nesne havuzu uygulamasını içerir. Bu sınıfın uyguladığı <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanını ile etkileşim kurmak için arabirim. EndpointDispatcher çağırdığında <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi, yeni bir örneğini oluşturmak yerine, özel uygulama var olan bir nesne, bellek havuzunda arar. Varsa, döndürülür. Aksi takdirde, `ObjectPoolInstanceProvider` denetler olmadığını `ActiveObjectsCount` özelliği (sayı havuzdan döndürülen nesnelerin) maksimum havuz boyutuna ulaştı. Değilse, yeni bir örneği oluşturulur ve çağırana döndürülen varsa ve `ActiveObjectsCount` sonradan artırılır. Aksi takdirde bir nesne oluşturma isteği, yapılandırılmış bir süre için sıraya alınır. Uygulamasını `GetObjectFromThePool` aşağıdaki örnek kodda gösterilmiştir.  
  
```  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 Özel `ReleaseInstance` uygulama havuzu ve azaltır için yayımlanan örneği ekler `ActiveObjectsCount` değeri. EndpointDispatcher farklı iş parçacıklarından bu yöntemleri çağırabilir ve bu nedenle sınıf düzeyinde üyelerine erişim eşitlenmiş `ObjectPoolInstanceProvider` sınıfı gereklidir.  
  
```  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 `ReleaseInstance` Yöntemi sağlayan bir *başlatma Temizleme* özelliği. Normalde havuza havuz ömrü boyunca nesnelerin en az sayıda tutar. Bununla birlikte, yapılandırmada belirtilen üst sınırına ulaşmadığınız havuzunda ek nesneleri oluşturma gerektiren aşırı kullanım dönemlerini olabilir. Sonunda havuzu daha az etkin duruma geldiğinde fazlalık nesneleri bir ek yükü olabilir. Bu nedenle, `activeObjectsCount` tetikler ve bir temizleme döngüsü gerçekleştiren boşta olan bir zamanlayıcı başlatıldığında sıfır ulaşır.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 ServiceModel katman uzantıları aşağıdaki davranışları kullanarak sayfaya bağlanır:  
  
-   Hizmet davranışları: Bunlar, tüm hizmet çalışma zamanı özelleştirme için izin verir.  
  
-   Uç nokta davranışları: Bu EndpointDispatcher dahil olmak üzere belirli bir hizmet uç noktası, özelleştirme yapma olanağı sağlar.  
  
-   Sözleşme davranışları: Bu özelleştirme ya da ile ilgili izin <xref:System.ServiceModel.Dispatcher.ClientRuntime> veya <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci veya hizmet sınıflarını, sırasıyla.  
  
-   İşlem davranışları: Bu özelleştirme ya da ile ilgili izin <xref:System.ServiceModel.Dispatcher.ClientOperation> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation> istemci veya hizmet sınıflarını, sırasıyla.  
  
 Uzantı havuzu bir nesne için bir uç nokta davranışı ya da bir hizmet davranışını oluşturulabilir. Bu örnekte, her Hizmeti uç noktası olanağı havuzu nesne geçerli bir hizmet davranışını kullanırız. Hizmet davranışları uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi. ServiceModel özel davranışlar haberdar olmak için birkaç yol vardır:  
  
-   Özel bir öznitelik kullanma.  
  
-   Kesin hizmet açıklaması'nın davranışları koleksiyonunuza ekleniyor.  
  
-   Yapılandırma dosyası genişletme.  
  
 Bu örnek bir özel öznitelik kullanır. Zaman <xref:System.ServiceModel.ServiceHost> olan yapılandırılmış, hizmetin türü tanımında kullanılan öznitelikler inceler ve kullanılabilir davranışlar hizmet açıklaması'nın davranışları koleksiyonuna ekler.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> Arabirim üç yöntem vardır: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Bu yöntem de WCF tarafından çağrıldığında, <xref:System.ServiceModel.ServiceHost> Başlatılmakta olan. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> ilk olarak adlandırılır; Bu tutarsızlıkları denetlenecek hizmeti sağlar. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> sonraki çağrılır; Bu yöntem, yalnızca çok Gelişmiş senaryolar gereklidir. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> Son olarak adlandırılır ve çalışma zamanı yapılandırma sorumludur. Aşağıdaki parametre olarak geçirilen <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
-   `Description`: Bu parametre, tüm hizmet hizmet açıklamasını sağlar. Bu hizmet uç noktaları, sözleşmeler, bağlamalar ve hizmetiyle ilişkili diğer veri hakkında açıklama verilerini incelemek için kullanılabilir.  
  
-   `ServiceHostBase`: Bu parametreyi sağlar <xref:System.ServiceModel.ServiceHostBase> başlatılan şu anda.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulama, yeni bir örneğini `ObjectPoolInstanceProvider` örneği ve atanan <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her bir özellik <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> için bağlı <xref:System.ServiceModel.ServiceHostBase>.  
  
```  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 Ek olarak bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulama `ObjectPoolingAttribute` sınıfı özniteliği bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üyelere sahiptir. Bu üyeleri içeren `MaxSize`, `MinSize`, `Enabled` ve `CreationTimeout`, .NET Enterprise Hizmetleri tarafından sağlanan havuzu nesne eşleştirilecek.  
  
 Davranış havuzu nesnesi artık bir WCF hizmeti için yeni oluşturulan özel hizmet uygulamasıyla açıklamalar eklenebilir `ObjectPooling` özniteliği.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Takma etkinleştirme ve devre dışı bırakma  
 Nesne havuzu oluşturma, birincil amacı, kısa süreli nesneleri görece pahalı oluşturma ve başlatma ile en iyi duruma getirme sağlamaktır. Bu nedenle bu uygulama düzgün şekilde kullandıysanız önemli ölçüde performans artışı verebilirsiniz. Havuzdan nesne döndürdüğünden, oluşturucu yalnızca bir kez çağrılır. Ancak, böylece bunlar başlatmak ve tek bir bağlam sırasında kullanılan kaynakları temizleme bazı uygulamalar, bazı denetim düzeyi gerektirir. Örneğin, bir küme hesaplama için kullanılan bir nesne, sonraki hesaplama işlenmeden önce özel alanları sıfırlayabilirsiniz. Kurumsal Hizmetler, geçersiz kılma nesne Geliştirici imkan vererek bu tür bir bağlama özel başlatma etkin `Activate` ve `Deactivate` yöntemlerinden <xref:System.EnterpriseServices.ServicedComponent> temel sınıfı.  
  
 Nesne havuzu çağrılarını `Activate` nesne havuzdan döndürmeden önce hemen yöntemi. `Deactivate` Nesne havuza geri döndüğünde çağrılır. <xref:System.EnterpriseServices.ServicedComponent> Ayrıca temel sınıfa sahip bir `boolean` adlı özellik `CanBePooled`, havuz nesnenin daha fazla havuza olup olmadığını bildirmek için kullanılabilir.  
  
 Bu işlev taklit etmek için ortak bir arabirim örneği bildirir (`IObjectControl`), yukarıda sözü edilen üye içermiyor. Bu arabirim, ardından sınıfları bağlam belirli başlatma sağlamaya yönelik hizmet tarafından uygulanır. <xref:System.ServiceModel.Dispatcher.IInstanceProvider> Uygulaması, bu gereksinimleri karşılayan değiştirilmelidir. Artık, her zaman size bir nesne çağırarak `GetInstance` yöntemi gerekir denetleyin nesne uygulayan olup olmadığını `IObjectControl.` aşması durumunda çağırmalısınız `Activate` yöntemi uygun şekilde.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Bir nesne havuza geri döndürülürken bir onay için gerekli `CanBePooled` nesnesi eklemeden önce özelliğini yeniden havuza.  
  
```  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 Hizmet Geliştirici, nesne havuzda toplanabilir karar verebilir çünkü nesne sayısı belirli bir zamanda havuzdaki en az boyutun altında gidebilirsiniz. Bu nedenle nesne sayısı en düşük düzeyin altına indi ve gerekli başlatma temizleme yordamı işaretlemeniz gerekir.  
  
```  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Her konsol penceresinde hizmet ve istemci kapatmak için Enter tuşuna basın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
