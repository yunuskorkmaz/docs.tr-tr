---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 897bb62df0a23073827aeed18b54bf77e8c6d4bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183604"
---
# <a name="instancing-initialization"></a>Başlatmayı Örneklendirme
Bu örnek, bir arabirim tanımlayarak [Havuzlama](../../../../docs/framework/wcf/samples/pooling.md) örneğini genişletir, `IObjectControl`bu da bir nesnenin başlatılmasını etkinleştirerek ve devre dışı kılarak özelleştirir. İstemci, nesneyi havuza döndüren ve nesneyi havuza döndürmeden yöntemler çağırır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
## <a name="extensibility-points"></a>Genişletilebilirlik Noktaları  
 Bir Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, kullanılacak genişletilebilirlik noktasına karar vermektir. WCF'de *EndpointDispatcher* terimi, gelen iletileri kullanıcının hizmetindeki yöntem çağrılarına dönüştürmekten ve bu yöntemden gelen bir iletiye dönüş değerlerini dönüştürmekten sorumlu bir çalışma zamanı bileşenini ifade eder. WCF hizmeti, her bitiş noktası için bir EndpointDispatcher oluşturur.  
  
 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> EndpointDispatcher, sınıfı kullanarak uç nokta kapsamı (hizmet tarafından alınan veya gönderilen tüm iletiler için) genişletilebilirlik sunar. Bu sınıf, EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenize olanak sağlar. Bu örnek, hizmet <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> sınıfının örneklerini sağlayan nesneyi işaret eden özelliğe odaklanır.  
  
## <a name="iinstanceprovider"></a>ıınstanceprovider  
 WCF'de, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi uygulayan bir örnek sağlayıcı kullanarak bir hizmet sınıfı örnekleri oluşturur. Bu arabirimin yalnızca iki yöntemi vardır:  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: İleti geldiğinde, Dispatcher iletiyi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi çağırır. Bu yönteme yapılan çağrıların <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> sıklığı özellik tarafından belirlenir. Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özellik , gelen her iletiyi işlemek için yeni bir hizmet <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> sınıfı örneği oluşturulacak şekilde ayarlanmışsa, ileti geldiğinde çağrılır. <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği iletiyi işlemeyi bitirdiğinde, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi çağırır. <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> Yöntemde olduğu gibi, bu yönteme yapılan çağrıların <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> sıklığı özellik tarafından belirlenir.  
  
## <a name="the-object-pool"></a>Nesne Havuzu  
 Sınıf `ObjectPoolInstanceProvider` nesne havuzu için uygulama içerir. Bu sınıf, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanı ile etkileşim için arabirimi uygular. EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi çağırdığında, yeni bir örnek oluşturmak yerine, özel uygulama bellek içi bir havuzda varolan bir nesneyi arar. Varsa, döndürülür. Aksi `ObjectPoolInstanceProvider` takdirde, `ActiveObjectsCount` özelliğin (havuzdan döndürülen nesne sayısı) maksimum havuz boyutuna ulaşıp ulaşmadığını denetler. Değilse, yeni bir örnek oluşturulur ve arayana döndürülür ve `ActiveObjectsCount` daha sonra artımlanır. Aksi takdirde, nesne oluşturma isteği yapılandırılmış bir süre için sıraya alınır. `GetObjectFromThePool` Uygulama aşağıdaki örnek kodda gösterilir.  
  
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
  
 Özel `ReleaseInstance` uygulama, serbest bırakılan örneği havuza geri ekler `ActiveObjectsCount` ve değeri eriter. EndpointDispatcher bu yöntemleri farklı iş iş parçacıklarından çağırabilir ve bu nedenle `ObjectPoolInstanceProvider` sınıftaki sınıf düzeyi üyelerine eşitlenmiş erişim gereklidir.  
  
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
  
 Yöntem, `ReleaseInstance` bir *temizleme başlatma* özelliği sağlar. Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar. Ancak, yapılandırmada belirtilen maksimum sınıra ulaşmak için havuzda ek nesneler oluşturmayı gerektiren aşırı kullanım dönemleri olabilir. Sonunda havuz daha az aktif hale geldiğinde bu artı nesneler ekstra bir ek yükü haline gelebilir. Bu nedenle `activeObjectsCount` sıfıra ulaştığında bir temizleme döngüsü tetikler ve gerçekleştirir bir boşta zamanlayıcı başlatılır.  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 ServiceModel katman uzantıları aşağıdaki davranışları kullanarak bağlanır:  
  
- Hizmet Davranışları: Bunlar, tüm hizmet çalışma zamanının özelleştirilmesine olanak sağlar.  
  
- Bitiş Noktası Davranışları: Bunlar, EndpointDispatcher da dahil olmak üzere belirli bir hizmet bitiş noktasının özelleştirilmesine olanak sağlar.  
  
- Sözleşme Davranışları: Bunlar, istemci veya <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> hizmetteki sınıfların sırasıyla özelleştirilmesine olanak sağlar.  
  
- İşlem Davranışları: Bunlar, istemci <xref:System.ServiceModel.Dispatcher.ClientOperation> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation> hizmetteki sınıfların sırasıyla özelleştirilmesine olanak sağlar.  
  
 Nesne birleştirme uzantısı amacıyla, bitiş noktası davranışı veya hizmet davranışı oluşturulabilir. Bu örnekte, nesne birleştirme yeteneğini hizmetin her bitiş noktasına uygulayan bir hizmet davranışı kullanırız. Hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulanarak oluşturulur. ServiceModel'i özel davranışlardan haberdar etmenin birkaç yolu vardır:  
  
- Özel bir öznitelik kullanma.  
  
- Zorunlu olarak hizmet açıklamasının davranış koleksiyonuna ekleme.  
  
- Yapılandırma dosyasını genişletme.  
  
 Bu örnek özel bir öznitelik kullanır. <xref:System.ServiceModel.ServiceHost> Oluşturulduğunda, hizmetin tür tanımında kullanılan öznitelikleri inceler ve hizmet açıklamasının davranış koleksiyonuna kullanılabilir davranışları ekler.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> Arabirimin üç yöntemi <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>vardır: ve . Bu yöntemler, başharflere <xref:System.ServiceModel.ServiceHost> alınırken WCF tarafından çağrılır. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>ilk denir; tutarsızlıklar için hizmetin denetlenmesini sağlar. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>sonraki denir; bu yöntem yalnızca çok gelişmiş senaryolarda gereklidir. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>sonuncu olarak adlandırılır ve çalışma süresini yapılandırmaktan sorumludur. Aşağıdaki parametreler e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>aktarılır:  
  
- `Description`: Bu parametre, tüm hizmet için hizmet açıklamasını sağlar. Bu, hizmetin bitiş noktaları, sözleşmeleri, bağlamaları ve hizmetle ilişkili diğer verilerle ilgili açıklama verilerini incelemek için kullanılabilir.  
  
- `ServiceHostBase`: Bu parametre, şu anda başharflere getirilmekte olan parametreyi <xref:System.ServiceModel.ServiceHostBase> sağlar.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamada, yeni bir `ObjectPoolInstanceProvider` örnek anında ve bağlı her <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> özellik <xref:System.ServiceModel.ServiceHostBase>atanır.  
  
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
  
 Bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulamaya ek `ObjectPoolingAttribute` olarak sınıf öznitelik bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üye vardır. Bu `MaxSize`üyeler, `MinSize` `Enabled` .NET Enterprise Services tarafından sağlanan nesne birleştirme özelliğini eşleştirmek için , ve `CreationTimeout`, içerir.  
  
 Nesne birleştirme davranışı artık yeni oluşturulan özel `ObjectPooling` öznitelik ile hizmet uygulaması açıklama yaparak bir WCF hizmetine eklenebilir.  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Hooking Aktivasyon ve Devre Dışı Bırakma  
 Nesne birleştirmenin birincil amacı, göreceli olarak pahalı oluşturma ve başlatma ile kısa ömürlü nesneleri en iyi duruma getirmektir. Bu nedenle, düzgün kullanıldığında bir uygulamaya önemli bir performans artışı sağlayabilir. Nesne havuzdan döndürüldinandığından, oluşturucu yalnızca bir kez çağrılır. Ancak, bazı uygulamalar, tek bir bağlam sırasında kullanılan kaynakları başlatma ve temizleme yapabilmeleri için bir miktar denetim gerektirir. Örneğin, bir hesaplama kümesi için kullanılan bir nesne, sonraki hesaplamayı işlemeden önce özel alanlarını sıfırlayabilir. Kurumsal Hizmetler, nesne geliştiricisinin ve `Activate` `Deactivate` yöntemleri <xref:System.EnterpriseServices.ServicedComponent> temel sınıftan geçersiz kılmasına izin vererek bu tür içeriğe özgü bir başlatma olanağı sağladı.  
  
 Nesne havuzu, `Activate` nesneyi havuzdan döndürmeden hemen önce yöntemi çağırır. `Deactivate`nesne havuza geri döndüğünde çağrılır. Taban sınıfın, nesnenin `CanBePooled`daha fazla havuza alınıp alınamayacağını havuza bildirmek için kullanılabilecek , adlı bir `boolean` özelliği de vardır. <xref:System.EnterpriseServices.ServicedComponent>  
  
 Bu işlevselliği taklit etmek için, örnek`IObjectControl`yukarıda belirtilen üyeleri olan bir ortak arabirim ( ) bildirir. Bu arabirim daha sonra bağlam belirli bir başlangıç sağlamak amacıyla hizmet sınıfları tarafından uygulanır. Uygulama, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> bu gereksinimleri karşılamak için değiştirilmelidir. Şimdi, `GetInstance` yöntemi çağırarak bir nesne almak her zaman, nesne `IObjectControl.` uygular eğer olup olmadığını `Activate` kontrol etmelisiniz, uygun şekilde yöntemi aramanız gerekir.  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Bir nesneyi havuza döndürdükten sonra, `CanBePooled` nesneyi havuza geri eklemeden önce özellik için bir denetim gerekir.  
  
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
  
 Hizmet geliştiricisi bir nesnenin bir araya gelip gelemeyeceğine karar verebildiği için, belirli bir zamanda havuzdaki nesne sayısı minimum boyutun altına inebilir. Bu nedenle, nesne sayısının minimum düzeyin altına inip gitmediğini kontrol etmeli ve temizleme yordamında gerekli başlatmaişlemini gerçekleştirmelisiniz.  
  
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
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Hizmeti ve istemciyi kapatmak için her konsol penceresinde Enter tuşuna basın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
