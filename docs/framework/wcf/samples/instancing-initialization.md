---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 06a8dfe571b652ded236df3097b37861c03a858d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596662"
---
# <a name="instancing-initialization"></a>Başlatmayı Örneklendirme
Bu örnek, bir arabirimini etkinleştirerek ve devre dışı bırakarak bir nesnenin başlatılmasını özelleştiren bir arabirim tanımlayarak [Havuz oluşturma](pooling.md) örneğini genişletir `IObjectControl` . İstemci, nesneyi havuza döndüren ve havuza nesne döndüren yöntemleri çağırır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="extensibility-points"></a>Genişletilebilirlik noktaları  
 Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasının kullanılmasına karar vermaktır. WCF 'de, *EndpointDispatcher* terimi, gelen iletileri kullanıcının hizmetinde Yöntem etkinleştirmeleri içine dönüştürmeden ve dönüş değerlerini Bu yöntemden giden bir iletiye dönüştürmekten sorumlu bir çalışma zamanı bileşenine başvurur. WCF hizmeti her uç nokta için bir EndpointDispatcher oluşturur.  
  
 EndpointDispatcher, sınıfını kullanarak uç nokta kapsamı (hizmet tarafından alınan veya gönderilen tüm iletiler için) sağlar <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> . Bu sınıf, EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenize olanak sağlar. Bu örnek, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örneklerini sağlayan nesnesine işaret eden özelliğine odaklanır.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 WCF 'de, EndpointDispatcher arabirimini uygulayan bir örnek sağlayıcı kullanarak bir hizmet sınıfının örneklerini oluşturur <xref:System.ServiceModel.Dispatcher.IInstanceProvider> . Bu arabirimin yalnızca iki yöntemi vardır:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Bir ileti geldiğinde, dağıtıcı <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak üzere yöntemini çağırır. Bu yönteme yapılan çağrıların sıklığı, özelliği tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> . Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği olarak ayarlandıysa <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType> , gelen her iletiyi işlemek için yeni bir hizmet sınıfı örneği oluşturulur, bu nedenle <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> ileti her geldiğinde çağrılır.  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği iletiyi işlemeyi tamamladığında, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemini çağırır. Yönteminde olduğu gibi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> , bu yönteme yapılan çağrıların sıklığı özelliği tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> .  
  
## <a name="the-object-pool"></a>Nesne havuzu  
 `ObjectPoolInstanceProvider`Sınıfı, nesne havuzu için uygulamayı içerir. Bu sınıf, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanıyla etkileşimde bulunmak için arabirimini uygular. EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi çağırdığında, yeni bir örnek oluşturmak yerine, özel uygulama bellek içi havuzda var olan bir nesneyi arar. Kullanılabilir bir tane varsa, döndürülür. Aksi takdirde, `ObjectPoolInstanceProvider` `ActiveObjectsCount` özelliğinin (havuzdan döndürülen nesne sayısı) en yüksek havuz boyutuna ulaştığından, bu özelliği denetler. Aksi takdirde, yeni bir örnek oluşturulup çağırana döndürülür ve `ActiveObjectsCount` daha sonra artırılır. Aksi takdirde, bir nesne oluşturma isteği yapılandırılmış bir süre için sıraya alınır. İçin uygulanması `GetObjectFromThePool` Aşağıdaki örnek kodda gösterilmiştir.  
  
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
  
 Özel `ReleaseInstance` uygulama, yayımlanan örneği havuza geri ekler ve `ActiveObjectsCount` değeri azaltır. EndpointDispatcher Bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle, sınıftaki sınıf düzeyi üyelerine eşitlenen erişim `ObjectPoolInstanceProvider` gerekir.  
  
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
  
 `ReleaseInstance`Yöntemi bir *Temizleme başlatma* özelliği sağlar. Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar. Ancak, yapılandırmada belirtilen en yüksek sınıra ulaşmak için havuzda ek nesneler oluşturulmasını gerektiren aşırı kullanım süreleri olabilir. Sonuç olarak, havuz daha az etkin hale geldiğinde, bu fazlalık nesneler ek bir ek yük haline gelebilir. Bu nedenle, `activeObjectsCount` bir boşta kalma süreölçeri sıfıra ulaştığında harekete geçiren ve Temizleme döngüsünü gerçekleştiren bir Zamanlayıcı başlatılır.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 ServiceModel katman uzantıları aşağıdaki davranışlar kullanılarak kullanıma alınır:  
  
- Hizmet davranışları: Bu, tüm hizmet çalışma zamanının özelleştirilmesine izin verir.  
  
- Uç nokta davranışları: Bu, EndpointDispatcher dahil olmak üzere belirli bir hizmet uç noktasının özelleştirilmesine izin verir.  
  
- Sözleşme davranışları: Bu, <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sırasıyla istemci veya hizmette bulunan ya da sınıfların özelleştirilmesine izin verir.  
  
- İşlem davranışları: Bu, <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> sırasıyla istemci veya hizmette bulunan ya da sınıfların özelleştirilmesine izin verir.  
  
 Bir nesne havuzu uzantısının amacı için bir uç nokta davranışı veya bir hizmet davranışı oluşturulabilir. Bu örnekte, hizmetin her uç noktasına nesne havuzu oluşturma özelliğini uygulayan bir hizmet davranışı kullanıyoruz. Hizmet davranışları arabirimi uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> . Özel davranışları ServiceModel olarak algılayan çeşitli yollar vardır:  
  
- Özel bir öznitelik kullanma.  
  
- Imperatively, hizmet açıklamasının davranış koleksiyonuna ekleniyor.  
  
- Yapılandırma dosyası genişletiliyor.  
  
 Bu örnek özel bir özniteliği kullanır. Oluşturulduğunda <xref:System.ServiceModel.ServiceHost> , hizmetin tür tanımında kullanılan öznitelikleri inceler ve kullanılabilir davranışları hizmet açıklamasının davranış koleksiyonuna ekler.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior>Arabirimin üç yöntemi vardır: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> . Bu yöntemler, başlatıldığında WCF tarafından çağırılır <xref:System.ServiceModel.ServiceHost> . <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>İlk olarak çağrılır; hizmetin tutarsızlıklar için inceleneme izin verir. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>sonraki çağırılır; Bu yöntem yalnızca Gelişmiş senaryolarda gereklidir. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>son olarak adlandırılır ve çalışma zamanının yapılandırılmasından sorumludur. Aşağıdaki parametreler içine geçirilir <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> :  
  
- `Description`: Bu parametre hizmetin tamamı için hizmet açıklamasını sağlar. Bu, hizmetin uç noktaları, sözleşmeleri, bağlamaları ve hizmetle ilişkili diğer verilerle ilgili açıklama verilerini denetlemek için kullanılabilir.  
  
- `ServiceHostBase`: Bu parametre, <xref:System.ServiceModel.ServiceHostBase> Şu anda başlatılmış olan ' i sağlar.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamada, öğesinin yeni bir örneği örneği oluşturulur `ObjectPoolInstanceProvider` ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> ' a iliştirilmiş her bir özelliğine atanır <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.ServiceHostBase> .  
  
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
  
 Bir uygulamaya ek olarak <xref:System.ServiceModel.Description.IServiceBehavior> , `ObjectPoolingAttribute` sınıfı öznitelik bağımsız değişkenlerini kullanarak nesne havuzunu özelleştirmek için çeşitli üyelere sahiptir. Bu Üyeler, `MaxSize` `MinSize` `Enabled` `CreationTimeout` .NET Enterprise Services tarafından sunulan nesne havuzu özellik kümesini eşleştirmek için, ve içerir.  
  
 Nesne havuzu oluşturma davranışı artık yeni oluşturulan özel öznitelikle hizmet uygulamasına ek olarak bir WCF hizmetine eklenebilir `ObjectPooling` .  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Etkinleştirme ve devre dışı bırakma  
 Nesne havuzunun birincil amacı, kısa süreli nesneleri görece maliyetli oluşturma ve başlatma ile optimize etmek. Bu nedenle, düzgün şekilde kullanılırsa uygulamaya çarpıcı bir performans artışı verebilir. Nesne havuzdan döndürüldüğünden, Oluşturucu yalnızca bir kez çağrılır. Ancak bazı uygulamalar, tek bir bağlam sırasında kullanılan kaynakları başlatıp temizleyebilecekleri bir denetim düzeyi gerektirir. Örneğin, bir hesaplamalar kümesi için kullanılan bir nesne, bir sonraki hesaplamayı işlemeden önce özel alanlarını sıfırlayabilir. Kurumsal Hizmetler, nesne geliştiricisi geçersiz kılınmasına `Activate` ve `Deactivate` temel sınıftan yöntemlere izin vererek bu tür içeriğe özgü başlatma işlemini etkinleştirdi <xref:System.EnterpriseServices.ServicedComponent> .  
  
 Nesne havuzu, `Activate` nesneyi havuzdan döndürmeden hemen önce yöntemini çağırır. `Deactivate`, nesne havuza geri dönzaman çağrılır. <xref:System.EnterpriseServices.ServicedComponent>Temel sınıf Ayrıca `boolean` adlı bir özelliğe sahiptir `CanBePooled` ve bu, havuzun daha fazla havuza kaydedilip edilmeyeceğini bildirmek için kullanılabilir.  
  
 Bu işlevselliği taklit etmek için örnek, belirtilen üyelere sahip ortak bir arabirim ( `IObjectControl` ) bildirir. Bu arabirim daha sonra içeriğe özgü başlatma sağlamak üzere amaçlanan hizmet sınıfları tarafından uygulanır. <xref:System.ServiceModel.Dispatcher.IInstanceProvider>Uygulamanın bu gereksinimleri karşılayacak şekilde değiştirilmesi gerekir. Şimdi, yöntemini çağırarak bir nesne aldığınızda, `GetInstance` nesnenin ne zaman uygulayıp uygulamadığını denetlemeniz gerekir `IObjectControl.` , `Activate` yöntemi uygun şekilde çağırmanız gerekir.  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Havuza bir nesne döndürürken, `CanBePooled` nesne havuza geri eklenmeden önce özelliği için bir denetim gereklidir.  
  
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
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
