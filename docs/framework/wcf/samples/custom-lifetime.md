---
title: Özel Yaşam Süresi
ms.date: 03/30/2017
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 1d9baa2d6eab476d5c8428208576f341e71fef2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-lifetime"></a>Özel Yaşam Süresi
Bu örnek, paylaşılan için özel yaşam süresi hizmetleri sağlayan bir Windows Communication Foundation (WCF) uzantısı yazmak gösterilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet örnekleri.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="shared-instancing"></a>Paylaşılan örnek oluşturma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet örneği için birkaç örneklemesini modu sunar. Bu konuda ele paylaşılan örnek oluşturma modu, bir hizmet örneği birden çok kanaldan arasında paylaşmak için bir yöntem sağlar. İstemcileri örneğinin uç noktası adresi yerel olarak gidermek veya hizmet uç noktası adresini çalışan bir örneği elde etmek için Üreteç yöntemi başvurun. Uç nokta adresi olduğunda, bunu yeni bir kanal oluşturmak ve iletişim başlatın. Aşağıdaki kod parçacığını bir istemci uygulaması var olan bir hizmet örneği için yeni bir kanal nasıl oluşturduğunu gösterir.  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 Diğer örneklemesini modları, paylaşılan örnekleme modunu hizmet örnekleri yayınlama benzersiz bir şekilde sahiptir. Tüm kanallar için bir örneği, hizmetin kapalı olduğunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı bir süreölçer başlatır. Zaman aşımı süresi dolmadan önce hiç kimsenin bağlantı yaparsa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örneğini serbest bırakır ve kaynak talepleri. Erdirme yordamının parçası olarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çağırır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi tüm <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> örneği serbest önce uygulamaları. Bunların tümünün dönerseniz `true` örneği yayımlanır. Aksi takdirde <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulamasıdır bilgilendirmek için sorumlu `Dispatcher` bir geri çağırma yöntemi kullanarak boşta durumu.  
  
 Varsayılan olarak, boşta kalma zaman aşımı değeri <xref:System.ServiceModel.InstanceContext> bir dakikadır. Ancak bu örnek, bu özel bir uzantısı kullanılarak nasıl genişletebilirsiniz gösterir.  
  
## <a name="extending-the-instancecontext"></a>InstanceContext genişletme  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> hizmet örneği arasında bağlantı ve `Dispatcher`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yeni bir durum veya davranışı, Genişletilebilir nesne desenine kullanarak ekleyerek bu çalışma zamanı bileşeni genişletmenizi sağlar. Genişletilebilir object deseni kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ya da mevcut çalışma zamanı sınıflarını yeni işlevselliği ile genişletmek veya yeni durumu özellik için bir nesne eklemek için. Genişletilebilir nesne modelinde üç arabirimi vardır: `IExtensibleObject<T>`, `IExtension<T>`, ve `IExtensionCollection<T>`.  
  
 `IExtensibleObject<T>` Arabirimi işlevleriyle özelleştirme uzantılarına izin vermek için nesneler tarafından gerçekleştirilir.  
  
 `IExtension<T>` Arabirimi türü sınıfların uzantıları olabilir nesneleri tarafından uygulanan `T`.  
  
 Ve son olarak, `IExtensionCollection<T>` arabirimidir koleksiyonu `IExtensions` izin veren almak için `IExtensions` türlerine göre.  
  
 Bu nedenle genişletmek için <xref:System.ServiceModel.InstanceContext> uygulamanız gereken `IExtension` arabirimi. Bu örnek projesinde `CustomLeaseExtension` sınıfı, bu uygulama içerir.  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 `IExtension` Arabirimi sahip iki yöntem `Attach` ve `Detach`. Çalışma zamanı ekler ve uzantı örneği ayırır adlarını kapsıyor gibi bu iki yöntem denir <xref:System.ServiceModel.InstanceContext> sınıfı. Bu örnekte `Attach` yöntemi izlemek için kullanılan <xref:System.ServiceModel.InstanceContext> geçerli uzantısı örneğine ait olduğu nesne.  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 Ayrıca, gerekli uygulama genişletilmiş ömrü desteği sağlamak için uzantı eklemeniz gerekir. Bu nedenle `ICustomLease` arabirimi istenen yöntemleriyle bildirilir ve uygulanan `CustomLeaseExtension` sınıfı.  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 Zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çağırır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yönteminde <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> bu çağrı için yönlendirilir uygulama <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi `CustomLeaseExtension`. Ardından `CustomLeaseExtension` özel durumu görmek için denetler olup olmadığını <xref:System.ServiceModel.InstanceContext> boştadır. Döndürür boşta ise `true`. Aksi halde, belirtilen bir genişletilmiş ömrü miktarı için bir süreölçer başlatır.  
  
```  
public bool IsIdle  
{  
  get  
  {  
    lock (thisLock)  
    {  
      if (isIdle)  
      {  
        return true;  
      }  
      else  
      {  
        StartTimer();  
        return false;  
      }  
    }  
  }  
}  
```  
  
 Zamanlayıcı'nın içinde `Elapsed` olay dağıtıcı geri çağırma işlevi başka temizleme döngüsü başlatmak için çağrılır.  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 Çalışan Zamanlayıcı boşta durumuna taşınan örneği için yeni bir ileti geldiğinde yenilemeye yolu yoktur.  
  
 Örnek uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> çağrıları kesmeye <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi ve rota onları `CustomLeaseExtension`. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Uygulama bulunduğu `CustomLifetimeLease` sınıfı. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Yöntemi çağrıldığında zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet örneği hakkında yayımlamayı amaçlamaktadır. Ancak, belirli bir yalnızca bir örneği var. `ISharedSessionInstance` ServiceBehavior'ın uygulamasında <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> koleksiyonu. Bu bilmesinin yolu yoktur anlamına gelir <xref:System.ServiceModel.InstanceContext> zaman kapatılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] denetler <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi. Bu nedenle bu örnek isteklerine serileştirmek için kilitleme iş parçacığı kullanan <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi.  
  
> [!IMPORTANT]
>  Seri hale getirme, uygulamanızın performansını önemli ölçüde etkileyebileceğinden iş parçacığı kilitleme kullanılarak önerilen yaklaşım değildir.  
  
 Özel üye değişkeni kullanılır `CustomLeaseExtension` izlemek için sınıf `IsIdle` değeri. Her zaman değerini <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> alınır `IsIdle` özel üye döndürülen ve Sıfırla `false`. Bu değer ayarlamak için gerekli olan `false` dağıtıcısı çağrıları emin olmak için <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemi.  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 Varsa `ISharedSessionLifetime.IsIdle` özelliği döndürür `false` dağıtıcı kullanarak bir geri çağırma işlevini kaydeder `NotifyIdle` yöntemi. Bu yöntem bir başvuru alır <xref:System.ServiceModel.InstanceContext> yayımlanan. Bu nedenle örnek kod sorgulayabilirsiniz `ICustomLease` uzantısı yazın ve denetleme `ICustomLease.IsIdle` Genişletilmiş durum özelliğini.  
  
```  
public void NotifyIdle(InstanceContextIdleCallback callback,   
            InstanceContext instanceContext)  
{  
    lock (thisLock)  
    {  
       ICustomLease customLease =  
           instanceContext.Extensions.Find<ICustomLease>();  
       customLease.Callback = callback;   
       isIdle = customLease.IsIdle;  
       if (isIdle)  
       {  
             callback(instanceContext);  
       }  
    }   
}  
```  
  
 Önce `ICustomLease.IsIdle` özellik geri çağırma özelliği bu için temel olarak ayarlanması gerekiyor işaretli `CustomLeaseExtension` boşta olduğunda göndereni bilgilendirmek için. Varsa `ICustomLease.IsIdle` döndürür `true`, `isIdle` özel üye kümesi yalnızca `CustomLifetimeLease` için `true` ve geri çağırma yöntemini çağırır. Kod bir kilidi tutan olduğundan başka bir iş parçacığı bu özel üyesinin değerini değiştiremezsiniz. Ve dağıtıcı denetlediğinde `ISharedSessionLifetime.IsIdle`, döndürdüğü `true` ve dağıtıcı örneği yayın olanak tanır.  
  
 Özel uzantı geçişteki tamamladığınıza göre hizmet modeli sayfaya içeriyor. Takma için `CustomLeaseExtension` uygulamasına <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sağlar <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> , önyükleme gerçekleştirmek için arabirim <xref:System.ServiceModel.InstanceContext>. Örnekte, `CustomLeaseInitializer` sınıfı bu arabirimi uygular ve bir örneğini ekler `CustomLeaseExtension` için <xref:System.ServiceModel.InstanceContext.Extensions%2A> tek yöntem başlatma koleksiyonundan. Bu yöntem tarafından dağıtıcısı başlatılırken çağrılır <xref:System.ServiceModel.InstanceContext>.  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 Son olarak `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` ve <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> uygulamalarıdır olduğu sayfaya kullanarak hizmet modeli kadar <xref:System.ServiceModel.Description.IServiceBehavior> uygulaması. Bu uygulama yerleştirilir `CustomLeaseTimeAttribute` sınıfı ve ayrıca türetilen `Attribute` temel sınıfı bu davranış bir öznitelik olarak kullanıma sunar. İçinde `IServiceBehavior.ApplyBehavior` yöntemi, örneklerini <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> ve `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` uygulamaları eklenir `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> koleksiyonları <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> sırasıyla.  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 Bu davranış ile açıklama ekleyerek bir örnek hizmet sınıfına eklenebilir `CustomLeaseTime` özniteliği.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a>Ayrıca Bkz.
