---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ae01254760219f2b408ef9d9663c4158e2802be8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="instancing-initialization"></a>Başlatmayı Örneklendirme
Bu örnek genişletir [toplama](../../../../docs/framework/wcf/samples/pooling.md) bir arabirim tanımlayarak örnek `IObjectControl`, etkinleştirme ve devre dışı bırakmadan nesneyi başlatma özelleştirir. İstemci, nesne havuza geri dönün ve, nesne havuzuna döndürmeyen yöntemleri çağırır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="extensibility-points"></a>Genişletilebilirlik noktaları  
 Bir Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasını kullanmak üzere karar vermektir. Wcf'de, terimi *EndpointDispatcher* sorumlu kullanıcının hizmet üzerinde yöntem çağrılarına gelen iletileri dönüştürme ve Giden iletiye Bu yöntemden dönüş değerleri dönüştürme için bir çalışma zamanı bileşeni başvurur . Bir WCF hizmeti bir EndpointDispatcher her bitiş noktasıyla ilgili oluşturur.  
  
 Uç nokta genişletilebilirlik kapsamı (alınan veya hizmet tarafından gönderilen tüm iletiler için) kullanarak EndpointDispatcher sunar <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> sınıfı. Bu sınıf EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenizi sağlar. Bu örnek odaklanır <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örnekleri sağlayan bir nesneye işaret etmiyor özelliği.  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 WCF'de, EndpointDispatcher uygulayan bir örnek sağlayıcısı kullanarak bir hizmet sınıfı örneklerini oluşturur <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi. Bu arabirim, yalnızca iki yöntemi vardır:  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Bir ileti geldiğinde, dağıtıcı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi. Bu yönteme çağrıları sıklığını tarafından belirlenen <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği. Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, hizmet sınıfının yeni bir örneğini, bunu ulaşan her iletiyi işlemek için oluşturulan <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> bir ileti ulaştığında çağrılır.  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği iletiyi işlemeyi bitirdikten sonra EndpointDispatcher çağırır <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi. Olarak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi, bu yönteme çağrıları sıklığını tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.  
  
## <a name="the-object-pool"></a>Nesne havuzu  
 `ObjectPoolInstanceProvider` Sınıf, nesne havuzu uygulamasını içerir. Bu sınıf uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanını ile etkileşim kurmak için arabirim. EndpointDispatcher çağırdığında <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yeni bir örneği oluşturmak yerine yöntemi, özel uygulama bellek içi havuzdaki var olan bir nesne arar. Varsa, döndürülür. Aksi takdirde, `ObjectPoolInstanceProvider` denetler olup olmadığını `ActiveObjectsCount` özelliği (havuzdan döndürülen nesne sayısı), en büyük havuz boyutuna ulaştı. Değilse, yeni bir örneği oluşturulur ve yapana varsa ve `ActiveObjectsCount` sonradan artırılır. Aksi halde bir nesne oluşturma isteği yapılandırılmış bir süre için sıraya alındı. Uygulamasını `GetObjectFromThePool` aşağıdaki örnek kodda gösterilir.  
  
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
  
 Özel `ReleaseInstance` uygulama havuzu ve azaltır için örnek yayınlandı ekler `ActiveObjectsCount` değeri. EndpointDispatcher bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle sınıf düzeyinde üyelerine erişimi eşitlenmiş `ObjectPoolInstanceProvider` sınıfı gereklidir.  
  
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
  
 `ReleaseInstance` Yöntemi sağlayan bir *başlatma Temizleme* özelliği. Normalde havuzu nesneler en az sayıda havuzu ömrü boyunca tutar. Ancak, yapılandırmada belirtilen en üst sınıra ulaşması havuzundaki ek nesneleri oluşturma gerektiren aşırı kullanım dönemlerini olabilir. Sonunda havuzu daha az etkin olduğunda fazlalık nesnelere ek yüke haline gelebilir. Bu nedenle, `activeObjectsCount` tetikler ve temizleme döngüsü gerçekleştiren bir boşta süreölçeri başlatılır sıfır ulaşır.  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 ServiceModel katman uzantıları aşağıdaki davranışları kullanarak sayfaya bağlanır:  
  
-   Hizmet davranışları: Bunlar tüm hizmet çalışma zamanı özelleştirmesi için izin verir.  
  
-   Uç nokta davranışları: Bunlar EndpointDispatcher dahil olmak üzere belirli hizmet uç noktası, özelleştirme için izin verir.  
  
-   Sözleşme davranışları: Bunlar için ya da özelleştirilmesine imkan tanımak <xref:System.ServiceModel.Dispatcher.ClientRuntime> veya <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci veya hizmet sırasıyla sınıfları.  
  
-   İşlemi davranışları: Bunlar için ya da özelleştirilmesine imkan tanımak <xref:System.ServiceModel.Dispatcher.ClientOperation> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation> istemci veya hizmet sırasıyla sınıfları.  
  
 Uzantı havuzu nesneyi amacıyla bir uç noktası davranışı ya da hizmet davranışı oluşturulabilir. Bu örnekte, tüm uç hizmetinin yeteneğini havuzu nesne geçerli bir hizmet davranışı kullanırız. Hizmet davranışları uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi. ServiceModel özel davranışlar haberdar olmak için birkaç yolu vardır:  
  
-   Özel bir öznitelik kullanma.  
  
-   İmperatively hizmet açıklaması 's davranışları koleksiyona ekleme.  
  
-   Yapılandırma dosyası genişletme.  
  
 Bu örnek özel bir öznitelik kullanır. Zaman <xref:System.ServiceModel.ServiceHost> olan oluşturulan, hizmetin tür tanımında kullanılan öznitelikler inceler ve kullanılabilir davranışları hizmet açıklaması 's davranışları koleksiyonuna ekler.  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> Arabirim üç yöntem vardır: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>. Bu yöntemlerin WCF tarafından çağrılması zaman <xref:System.ServiceModel.ServiceHost> başlatıldığını. <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> ilk olarak adlandırılır; tutarsızlıkları denetlenecek hizmeti sağlar. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> sonraki çağrılır; Bu yöntem yalnızca çok Gelişmiş senaryolarda gereklidir. <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> Son olarak adlandırılır ve çalışma zamanı yapılandırmak için sorumludur. Aşağıdaki parametreleri içine geçirilir <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:  
  
-   `Description`: Bu parametre, tüm hizmet hizmet açıklamasını sağlar. Bu hizmetin uç noktaları, sözleşmeler, bağlamaları ve hizmeti ile ilişkili diğer veri hakkında açıklama verilerini incelemek için kullanılabilir.  
  
-   `ServiceHostBase`: Bu parametre sağlar <xref:System.ServiceModel.ServiceHostBase> , şu anda başlatılır.  
  
 Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulaması, yeni bir örneğini `ObjectPoolInstanceProvider` örneği ve atanan <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her bir özellik <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> için bağlı <xref:System.ServiceModel.ServiceHostBase>.  
  
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
  
 Ek olarak bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulama `ObjectPoolingAttribute` sınıfı öznitelik bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üye sahiptir. Bu üyeleri dahil `MaxSize`, `MinSize`, `Enabled` ve `CreationTimeout`, .NET Enterprise Hizmetleri tarafından sağlanan özellik kümesi havuzu nesne eşleşecek şekilde.  
  
 Davranış havuzu nesne artık bir WCF hizmetine yeni oluşturulan özel hizmet uygulamasıyla yorumlama tarafından eklenebilir `ObjectPooling` özniteliği.  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>Takma etkinleştirme ve devre dışı bırakma  
 Nesne havuzu oluşturma, birincil amacı, kısa süreli nesneler görece pahalı oluşturma ve başlatma ile en iyi duruma getirme sağlamaktır. Bu nedenle önemli ölçüde performans artışı düzgün kullandıysanız uygulamaya verebilirsiniz. Nesne havuzdan döndürdüğünden Oluşturucusu yalnızca bir kez çağrılır. Ancak, böylece bunlar başlatmak ve tek bir bağlam sırasında kullanılan kaynakları temizleme bazı uygulamalar belirli bir düzeyde denetimi gerektirir. Örneğin, bir hesaplama kümesi için kullanılan bir nesne, sonraki hesaplama işlemeden önce özel alanları sıfırlayabilirsiniz. Kurumsal Hizmetler geçersiz kılma nesne Geliştirici izin vererek bu tür bir bağlama özgü başlatma etkin `Activate` ve `Deactivate` yöntemleri <xref:System.EnterpriseServices.ServicedComponent> temel sınıfı.  
  
 Nesne havuzu çağrılarını `Activate` havuzdan nesnesi döndüren hemen önce yöntemi. `Deactivate` Nesne havuza geri döndüğünde adı verilir. <xref:System.EnterpriseServices.ServicedComponent> Temel sınıfı da sahip bir `boolean` adlı özellik `CanBePooled`, havuzu nesne daha fazla havuza olup olmadığını bildirmek için kullanılabilir.  
  
 Bu işlev taklit etmek üzere ortak bir arabirim örnek bildirir (`IObjectControl`), daha önce bahsedilen üyeler içeriyor. Bu arabirim, ardından sınıfları bağlam belirli başlatma sağlamaya yönelik hizmeti tarafından uygulanır. <xref:System.ServiceModel.Dispatcher.IInstanceProvider> Uygulaması bu gereksinimleri karşılamak için değiştirilmesi gerekir. Şimdi, her zaman size bir nesne çağırarak `GetInstance` yöntemi, kontrol gerekir nesne uygulayan olup olmadığını `IObjectControl.` aşması durumunda çağırmalısınız `Activate` yöntemi uygun şekilde.  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 Bir nesne havuza geri döndürülürken bir onay için gereken `CanBePooled` nesne eklemeden önce özelliğini yeniden havuzuna.  
  
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
  
 Hizmet Geliştirici nesneyi havuza olup olmadığını karar verebilirsiniz çünkü nesne sayısı belirli bir zamanda havuzunda en az boyutun altında gidebilirsiniz. Bu nedenle nesne sayısı en düşük düzeyin altına indi ve gerekli başlatma temizleme yordamı işaretlemeniz gerekir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a>Ayrıca Bkz.
