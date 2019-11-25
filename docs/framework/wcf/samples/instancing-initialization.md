---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 44cd278fb0e48e07562b0b8ad52855b4a3f70761
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975870"
---
# <a name="instancing-initialization"></a>Başlatmayı Örneklendirme
Bu örnek, bir arabirimini etkinleştirerek ve devre dışı bırakarak bir nesnenin başlatılmasını özelleştiren `IObjectControl`bir arabirim tanımlayarak [Havuz](../../../../docs/framework/wcf/samples/pooling.md) örneğini genişletir. İstemci, nesneyi havuza döndüren ve havuza nesne döndüren yöntemleri çağırır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="extensibility-points"></a>Genişletilebilirlik noktaları  
 Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasının kullanılmasına karar vermaktır. WCF 'de, *EndpointDispatcher* terimi, gelen iletileri kullanıcının hizmetinde Yöntem etkinleştirmeleri içine dönüştürmeden ve dönüş değerlerini Bu yöntemden giden bir iletiye dönüştürmekten sorumlu bir çalışma zamanı bileşenine başvurur. WCF hizmeti her uç nokta için bir EndpointDispatcher oluşturur.  
  
 EndpointDispatcher, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> sınıfını kullanarak uç nokta kapsamı (hizmetin aldığı veya hizmet tarafından gönderilen tüm iletiler için) sağlar. Bu sınıf, EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenize olanak sağlar. Bu örnek, hizmet sınıfının örneklerini sağlayan nesnesine işaret eden <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> özelliğine odaklanır.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 WCF 'de, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimini uygulayan bir örnek sağlayıcısı kullanarak bir hizmet sınıfının örneklerini oluşturur. Bu arabirimin yalnızca iki yöntemi vardır:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: bir ileti geldiğinde dağıtıcı, iletiyi işlemek üzere hizmet sınıfının bir örneğini oluşturmak için <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemini çağırır. Bu yönteme yapılan çağrıların sıklığı <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği tarafından belirlenir. Örneğin <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>olarak ayarlanırsa, gelen her iletiyi işlemek için yeni bir hizmet sınıfı örneği oluşturulur, bu nedenle <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> ileti geldiğinde çağrılır.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: hizmet örneği iletiyi işlemeyi tamamladığında, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemini çağırır. <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yönteminde olduğu gibi, bu yönteme yapılan çağrıların sıklığı <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği tarafından belirlenir.  
  
## <a name="the-object-pool"></a>Nesne havuzu  
 `ObjectPoolInstanceProvider` sınıfı, nesne havuzunun uygulamasını içerir. Bu sınıf, hizmet modeli katmanıyla etkileşimde bulunmak için <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimini uygular. EndpointDispatcher, yeni bir örnek oluşturmak yerine <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemini çağırdığında, özel uygulama bellek içi havuzda var olan bir nesneyi arar. Kullanılabilir bir tane varsa, döndürülür. Aksi takdirde, `ActiveObjectsCount` özelliğinin (havuzdan döndürülen nesne sayısı) en yüksek havuz boyutuna ulaştığından `ObjectPoolInstanceProvider` denetler. Aksi takdirde, yeni bir örnek oluşturulur ve çağırana döndürülür ve `ActiveObjectsCount` daha sonra artırılır. Aksi takdirde, bir nesne oluşturma isteği yapılandırılmış bir süre için sıraya alınır. `GetObjectFromThePool` uygulanması aşağıdaki örnek kodda gösterilmiştir.  
  
```csharp
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
  
 Özel `ReleaseInstance` uygulama, yayımlanan örneği havuza geri ekler ve `ActiveObjectsCount` değerini azaltır. EndpointDispatcher Bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle `ObjectPoolInstanceProvider` sınıfındaki sınıf düzeyi üyelerine eşitlenen erişim gereklidir.  
  
```csharp
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
  
 `ReleaseInstance` yöntemi bir *Temizleme başlatma* özelliği sağlar. Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar. Ancak, yapılandırmada belirtilen en yüksek sınıra ulaşmak için havuzda ek nesneler oluşturulmasını gerektiren aşırı kullanım süreleri olabilir. Sonuç olarak, havuz daha az etkin hale geldiğinde, bu fazlalık nesneler ek bir ek yük haline gelebilir. Bu nedenle `activeObjectsCount` sıfırdan ulaştığında bir boşta kalma süreölçeri tetiklenir ve Temizleme döngüsünü gerçekleştirir.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 ServiceModel katman uzantıları aşağıdaki davranışlar kullanılarak kullanıma alınır:  
  
- Hizmet davranışları: Bu, tüm hizmet çalışma zamanının özelleştirilmesine izin verir.  
  
- Uç nokta davranışları: Bu, EndpointDispatcher dahil olmak üzere belirli bir hizmet uç noktasının özelleştirilmesine izin verir.  
  
- Sözleşme davranışları: Bu, sırasıyla istemci veya hizmette <xref:System.ServiceModel.Dispatcher.ClientRuntime> ya da <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfların özelleştirilmesine izin verir.  
  
- İşlem davranışları: Bu, sırasıyla istemci veya hizmette <xref:System.ServiceModel.Dispatcher.ClientOperation> ya da <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfların özelleştirilmesine izin verir.  
  
 Bir nesne havuzu uzantısının amacı için bir uç nokta davranışı veya bir hizmet davranışı oluşturulabilir. Bu örnekte, hizmetin her uç noktasına nesne havuzu oluşturma özelliğini uygulayan bir hizmet davranışı kullanıyoruz. Hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulayarak oluşturulur. Özel davranışları ServiceModel olarak algılayan çeşitli yollar vardır:  
  
- Özel bir öznitelik kullanma.  
  
- Imperatively, hizmet açıklamasının davranış koleksiyonuna ekleniyor.  
  
- Yapılandırma dosyası genişletiliyor.  
  
 Bu örnek özel bir özniteliği kullanır. <xref:System.ServiceModel.ServiceHost> oluşturulduğunda, hizmetin tür tanımında kullanılan öznitelikleri inceler ve kullanılabilir davranışları hizmet açıklamasının davranış koleksiyonuna ekler.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi üç yönteme sahiptir: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. <xref:System.ServiceModel.ServiceHost> başlatıldığında bu yöntemler WCF tarafından çağırılır. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> ilk olarak çağrılır; hizmetin tutarsızlıklar için inceleneme izin verir. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> daha sonra çağrılır; Bu yöntem yalnızca Gelişmiş senaryolarda gereklidir. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> son olarak adlandırılır ve çalışma zamanının yapılandırılmasından sorumludur. Aşağıdaki parametreler <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>geçirilir:  
  
- `Description`: Bu parametre hizmetin tamamı için hizmet açıklamasını sağlar. Bu, hizmetin uç noktaları, sözleşmeleri, bağlamaları ve hizmetle ilişkili diğer verilerle ilgili açıklama verilerini denetlemek için kullanılabilir.  
  
- `ServiceHostBase`: Bu parametre, şu anda başlatılmış olan <xref:System.ServiceModel.ServiceHostBase> sağlar.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamasında, yeni bir `ObjectPoolInstanceProvider` örneği oluşturulur ve <xref:System.ServiceModel.ServiceHostBase>eklenen her <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> özelliğine atanır.  
  
```csharp
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
  
 <xref:System.ServiceModel.Description.IServiceBehavior> uygulamasına ek olarak, `ObjectPoolingAttribute` sınıfı, nesne havuzunu öznitelik bağımsız değişkenlerini kullanarak özelleştirmek için çeşitli üyelere sahiptir. Bu Üyeler, .NET Enterprise Services tarafından sunulan nesne havuzu özellik kümesiyle eşleşecek `MaxSize`, `MinSize`, `Enabled` ve `CreationTimeout`içerir.  
  
 Nesne havuzu oluşturma davranışı artık yeni oluşturulan özel `ObjectPooling` özniteliğiyle hizmet uygulamasına ek olarak bir WCF hizmetine eklenebilir.  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Etkinleştirme ve devre dışı bırakma  
 Nesne havuzunun birincil amacı, kısa süreli nesneleri görece maliyetli oluşturma ve başlatma ile optimize etmek. Bu nedenle, düzgün şekilde kullanılırsa uygulamaya çarpıcı bir performans artışı verebilir. Nesne havuzdan döndürüldüğünden, Oluşturucu yalnızca bir kez çağrılır. Ancak bazı uygulamalar, tek bir bağlam sırasında kullanılan kaynakları başlatıp temizleyebilecekleri bir denetim düzeyi gerektirir. Örneğin, bir hesaplamalar kümesi için kullanılan bir nesne, bir sonraki hesaplamayı işlemeden önce özel alanlarını sıfırlayabilir. Kurumsal Hizmetler, nesne geliştiricisinin <xref:System.EnterpriseServices.ServicedComponent> taban sınıfından `Activate` ve `Deactivate` yöntemleri geçersiz kılmasına izin vererek bu tür içeriğe özgü başlatma işlemini etkinleştirdi.  
  
 Nesne havuzu, nesneyi havuzdan döndürmeden hemen önce `Activate` yöntemini çağırır. `Deactivate`, nesne havuza geri dönzaman çağrılır. <xref:System.EnterpriseServices.ServicedComponent> temel sınıfı `CanBePooled`adlı bir `boolean` özelliğine sahiptir ve bu, havuzun daha fazla havuza eklenip eklenmeyeceğini bildirmek için de kullanılabilir.  
  
 Bu işlevselliği taklit etmek için örnek, belirtilen üyelere sahip ortak bir arabirim (`IObjectControl`) bildirir. Bu arabirim daha sonra içeriğe özgü başlatma sağlamak üzere amaçlanan hizmet sınıfları tarafından uygulanır. <xref:System.ServiceModel.Dispatcher.IInstanceProvider> uygulamasının bu gereksinimleri karşılayacak şekilde değiştirilmesi gerekir. Artık `GetInstance` yöntemini çağırarak bir nesne aldığınızda, nesnenin `IObjectControl.` uygulayıp uygulamadığını denetlemeniz gerekir, `Activate` yöntemini uygun şekilde çağırmanız gerekir.  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Havuza bir nesne döndürürken, nesne havuza geri eklenmeden önce `CanBePooled` özelliği için bir denetim gereklidir.  
  
```csharp  
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
  
 Hizmet geliştiricisi bir nesnenin havuza kaydedilip edilmeyeceğini belirleyebildiğinden, havuzdaki belirli bir zamanda bulunan nesne sayısı en düşük boyutun altına gidebilir. Bu nedenle, nesne sayısının en düşük düzeyin altında olup olmadığını ve Temizleme yordamında gerekli başlatmayı gerçekleştirip gerçekleştirmediğini denetlemeniz gerekir.  
  
```csharp  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
