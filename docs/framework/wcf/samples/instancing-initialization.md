---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: f97a8b6723224b73476f84703ec3975abff0b476
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931032"
---
# <a name="instancing-initialization"></a>Başlatmayı Örneklendirme
Bu örnek, bir arabirimini etkinleştirerek ve devre dışı bırakarak bir `IObjectControl`nesnenin başlatılmasını özelleştiren bir arabirim tanımlayarak [Havuz oluşturma](../../../../docs/framework/wcf/samples/pooling.md) örneğini genişletir. İstemci, nesneyi havuza döndüren ve havuza nesne döndüren yöntemleri çağırır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="extensibility-points"></a>Genişletilebilirlik noktaları  
 Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasının kullanılmasına karar vermaktır. WCF 'de, *EndpointDispatcher* terimi, gelen iletileri kullanıcının hizmetinde Yöntem etkinleştirmeleri içine dönüştürmeden ve dönüş değerlerini Bu yöntemden giden bir iletiye dönüştürmekten sorumlu bir çalışma zamanı bileşenine başvurur. WCF hizmeti her uç nokta için bir EndpointDispatcher oluşturur.  
  
 EndpointDispatcher, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> sınıfını kullanarak uç nokta kapsamı (hizmet tarafından alınan veya gönderilen tüm iletiler için) sağlar. Bu sınıf, EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenize olanak sağlar. Bu örnek, hizmet sınıfının <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> örneklerini sağlayan nesnesine işaret eden özelliğine odaklanır.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 WCF 'de, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimini uygulayan bir örnek sağlayıcı kullanarak bir hizmet sınıfının örneklerini oluşturur. Bu arabirimin yalnızca iki yöntemi vardır:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Bir ileti geldiğinde, dağıtıcı iletiyi işlemek için hizmet <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> sınıfının bir örneğini oluşturmak üzere yöntemini çağırır. Bu yönteme yapılan çağrıların sıklığı, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği tarafından belirlenir. Örneğin <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> , özelliği olarak <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>ayarlandıysa, gelen her iletiyi işlemek için yeni bir hizmet sınıfı örneği oluşturulur, bu nedenle <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> ileti her geldiğinde çağrılır.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği iletiyi işlemeyi tamamladığında, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemini çağırır. Yönteminde olduğu gibi, bu yönteme yapılan çağrıların sıklığı <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği tarafından belirlenir. <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>  
  
## <a name="the-object-pool"></a>Nesne havuzu  
 `ObjectPoolInstanceProvider` Sınıfı, nesne havuzu için uygulamayı içerir. Bu sınıf, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanıyla etkileşimde bulunmak için arabirimini uygular. EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi çağırdığında, yeni bir örnek oluşturmak yerine, özel uygulama bellek içi havuzda var olan bir nesneyi arar. Kullanılabilir bir tane varsa, döndürülür. Aksi takdirde `ObjectPoolInstanceProvider` , `ActiveObjectsCount` özelliğinin (havuzdan döndürülen nesne sayısı) en yüksek havuz boyutuna ulaştığından, bu özelliği denetler. Aksi takdirde, yeni bir örnek oluşturulup çağırana döndürülür ve `ActiveObjectsCount` daha sonra artırılır. Aksi takdirde, bir nesne oluşturma isteği yapılandırılmış bir süre için sıraya alınır. İçin `GetObjectFromThePool` uygulanması aşağıdaki örnek kodda gösterilmiştir.  
  
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
  
 Özel `ReleaseInstance` uygulama, yayımlanan örneği havuza geri ekler ve `ActiveObjectsCount` değeri azaltır. EndpointDispatcher Bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle, `ObjectPoolInstanceProvider` sınıftaki sınıf düzeyi üyelerine eşitlenen erişim gerekir.  
  
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
  
 Yöntemi bir temizleme başlatma özelliği sağlar. `ReleaseInstance` Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar. Ancak, yapılandırmada belirtilen en yüksek sınıra ulaşmak için havuzda ek nesneler oluşturulmasını gerektiren aşırı kullanım süreleri olabilir. Sonuç olarak, havuz daha az etkin hale geldiğinde, bu fazlalık nesneler ek bir ek yük haline gelebilir. Bu nedenle, `activeObjectsCount` bir boşta kalma süreölçeri sıfıra ulaştığında harekete geçiren ve Temizleme döngüsünü gerçekleştiren bir Zamanlayıcı başlatılır.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 ServiceModel katman uzantıları aşağıdaki davranışlar kullanılarak kullanıma alınır:  
  
- Hizmet davranışları: Bu, tüm hizmet çalışma zamanının özelleştirilmesine izin verir.  
  
- Uç nokta davranışları: Bu, EndpointDispatcher dahil olmak üzere belirli bir hizmet uç noktasının özelleştirilmesine izin verir.  
  
- Sözleşme davranışları: Bunlar, sırasıyla istemci veya hizmette bulunan <xref:System.ServiceModel.Dispatcher.ClientRuntime> ya <xref:System.ServiceModel.Dispatcher.DispatchRuntime> da sınıfların özelleştirilmesine olanak sağlar.  
  
- İşlem davranışları: Bunlar, sırasıyla istemci veya hizmette bulunan <xref:System.ServiceModel.Dispatcher.ClientOperation> ya <xref:System.ServiceModel.Dispatcher.DispatchOperation> da sınıfların özelleştirilmesine olanak sağlar.  
  
 Bir nesne havuzu uzantısının amacı için bir uç nokta davranışı veya bir hizmet davranışı oluşturulabilir. Bu örnekte, hizmetin her uç noktasına nesne havuzu oluşturma özelliğini uygulayan bir hizmet davranışı kullanıyoruz. Hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulayarak oluşturulur. Özel davranışları ServiceModel olarak algılayan çeşitli yollar vardır:  
  
- Özel bir öznitelik kullanma.  
  
- Imperatively, hizmet açıklamasının davranış koleksiyonuna ekleniyor.  
  
- Yapılandırma dosyası genişletiliyor.  
  
 Bu örnek özel bir özniteliği kullanır. <xref:System.ServiceModel.ServiceHost> Oluşturulduğunda, hizmetin tür tanımında kullanılan öznitelikleri inceler ve kullanılabilir davranışları hizmet açıklamasının davranış koleksiyonuna ekler.  
  
 `,` Arabiriminüç`,` yöntemi vardır: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>ve. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> <xref:System.ServiceModel.Description.IServiceBehavior> <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Bu yöntemler, <xref:System.ServiceModel.ServiceHost> başlatıldığında WCF tarafından çağırılır. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>İlk olarak çağrılır; hizmetin tutarsızlıklar için inceleneme izin verir. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>sonraki çağırılır; Bu yöntem yalnızca Gelişmiş senaryolarda gereklidir. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>son olarak adlandırılır ve çalışma zamanının yapılandırılmasından sorumludur. Aşağıdaki parametreler içine <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>geçirilir:  
  
- `Description`: Bu parametre tüm hizmet için hizmet açıklamasını sağlar. Bu, hizmetin uç noktaları, sözleşmeleri, bağlamaları ve hizmetle ilişkili diğer verilerle ilgili açıklama verilerini denetlemek için kullanılabilir.  
  
- `ServiceHostBase`: Bu parametre, <xref:System.ServiceModel.ServiceHostBase> Şu anda başlatılmış olan öğesini sağlar.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamada, öğesinin `ObjectPoolInstanceProvider` yeni bir örneği örneği oluşturulur ve ' a iliştirilmiş her <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.ServiceHostBase>özelliğine atanır.  
  
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
  
 Bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulamaya ek olarak, `ObjectPoolingAttribute` sınıfı öznitelik bağımsız değişkenlerini kullanarak nesne havuzunu özelleştirmek için çeşitli üyelere sahiptir. Bu Üyeler, `MaxSize`.NET Enterprise `Enabled` Services tarafından sunulan nesne havuzu özellik kümesini eşleştirmek için, ve `CreationTimeout`içerir `MinSize`.  
  
 Nesne havuzu oluşturma davranışı artık yeni oluşturulan özel `ObjectPooling` öznitelikle hizmet uygulamasına ek olarak bir WCF hizmetine eklenebilir.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Etkinleştirme ve devre dışı bırakma  
 Nesne havuzunun birincil amacı, kısa süreli nesneleri görece maliyetli oluşturma ve başlatma ile optimize etmek. Bu nedenle, düzgün şekilde kullanılırsa uygulamaya çarpıcı bir performans artışı verebilir. Nesne havuzdan döndürüldüğünden, Oluşturucu yalnızca bir kez çağrılır. Ancak bazı uygulamalar, tek bir bağlam sırasında kullanılan kaynakları başlatıp temizleyebilecekleri bir denetim düzeyi gerektirir. Örneğin, bir hesaplamalar kümesi için kullanılan bir nesne, bir sonraki hesaplamayı işlemeden önce özel alanlarını sıfırlayabilir. Kurumsal Hizmetler, nesne geliştiricisi geçersiz kılınmasına `Activate` ve `Deactivate` <xref:System.EnterpriseServices.ServicedComponent> temel sınıftan yöntemlere izin vererek bu tür içeriğe özgü başlatma işlemini etkinleştirdi.  
  
 Nesne havuzu, nesneyi havuzdan `Activate` döndürmeden hemen önce yöntemini çağırır. `Deactivate`, nesne havuza geri dönzaman çağrılır. Temel sınıf ayrıca adlı `boolean` `CanBePooled`bir özelliğe sahiptir ve bu, havuzun daha fazla havuza kaydedilip edilmeyeceğini bildirmek için kullanılabilir. <xref:System.EnterpriseServices.ServicedComponent>  
  
 Bu işlevselliği taklit etmek için örnek, belirtilen üyelere sahip ortak bir`IObjectControl`Arabirim () bildirir. Bu arabirim daha sonra içeriğe özgü başlatma sağlamak üzere amaçlanan hizmet sınıfları tarafından uygulanır. <xref:System.ServiceModel.Dispatcher.IInstanceProvider> Uygulamanın bu gereksinimleri karşılayacak şekilde değiştirilmesi gerekir. Şimdi, `GetInstance` yöntemini çağırarak bir nesne aldığınızda, nesnenin ne zaman uygulayıp uygulamadığını `IObjectControl.` denetlemeniz gerekir `Activate` , yöntemi uygun şekilde çağırmanız gerekir.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Havuza bir nesne döndürürken, nesne havuza geri eklenmeden önce `CanBePooled` özelliği için bir denetim gereklidir.  
  
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
  
 Hizmet geliştiricisi bir nesnenin havuza kaydedilip edilmeyeceğini belirleyebildiğinden, havuzdaki belirli bir zamanda bulunan nesne sayısı en düşük boyutun altına gidebilir. Bu nedenle, nesne sayısının en düşük düzeyin altında olup olmadığını ve Temizleme yordamında gerekli başlatmayı gerçekleştirip gerçekleştirmediğini denetlemeniz gerekir.  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
