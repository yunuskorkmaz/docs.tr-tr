---
title: Özel ömür
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 8625877d9b4d05d5cf06af2c9f8ef10f701e98db
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715472"
---
# <a name="custom-lifetime"></a>Özel ömür

Bu örnek, paylaşılan WCF hizmet örnekleri için özel ömür hizmetleri sağlamak üzere bir Windows Communication Foundation (WCF) uzantısının nasıl yazılacağını gösterir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri Bu makalenin sonunda bulunur.

## <a name="shared-instancing"></a>Paylaşılan örnek oluşturma

WCF, hizmet örneklerinizin çeşitli örnek oluşturma modlarını sunar. Bu makalede ele alınan paylaşılan örnek oluşturma modu, bir hizmet örneğini birden çok kanal arasında paylaşmak için bir yol sağlar. İstemciler, hizmette bir fabrika yöntemiyle iletişim kurabilirler ve iletişim başlatmak için yeni bir kanal oluşturabilir. Aşağıdaki kod parçacığı, bir istemci uygulamanın var olan bir hizmet örneğine nasıl yeni bir kanal oluşturduğunu gösterir:

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

Diğer örnek oluşturma modlarının aksine, paylaşılan örnek oluşturma modunun hizmet örneklerini serbest bırakma yöntemine özgü bir yolu vardır. Varsayılan olarak, tüm kanallar bir <xref:System.ServiceModel.InstanceContext>için kapatıldığında, WCF hizmeti çalışma zamanı, hizmet <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerCall> veya <xref:System.ServiceModel.InstanceContextMode.PerSession>olarak yapılandırılıp yapılandırılmadığını denetler ve bu durumda örneği serbest bırakır ve kaynakları talep eder. Özel bir <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kullanılıyorsa, WCF örneği serbest bırakmadan önce sağlayıcı uygulamasının <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemini çağırır. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>, örnek `true` döndürürse <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulama, bir geri çağırma yöntemi kullanarak boşta durumunun `Dispatcher` bildirilmekten sorumludur. Bu, sağlayıcının <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemi çağırarak yapılır.

Bu örnek, boşta kalma zaman aşımı olan 20 saniyelik <xref:System.ServiceModel.InstanceContext> serbest bırakmayı nasıl erteleyebileceğinizi gösterir.

## <a name="extending-the-instancecontext"></a>InstanceContext 'i genişletme

WCF 'de, <xref:System.ServiceModel.InstanceContext> hizmet örneği ve `Dispatcher`arasındaki bağlantıdır. WCF, genişletilebilir nesne düzenlerini kullanarak bu çalışma zamanı bileşenini yeni durum veya davranış ekleyerek genişletmenizi sağlar. Genişletilebilir nesne stili, mevcut çalışma zamanı sınıflarını yeni işlevlerle genişletmek ya da bir nesneye yeni durum özellikleri eklemek için WCF 'de kullanılır. Genişletilebilir nesne deseninin üç arabirimi vardır: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>ve <xref:System.ServiceModel.IExtensionCollection%601>.

<xref:System.ServiceModel.IExtensibleObject%601> arabirimi, işlevlerini özelleştiren uzantılara izin vermek için nesneleri tarafından uygulanır.

<xref:System.ServiceModel.IExtension%601> arabirimi, `T`türündeki sınıfların uzantıları olabilecek nesneler tarafından uygulanır.

Son olarak <xref:System.ServiceModel.IExtensionCollection%601> arabirimi, bir <xref:System.ServiceModel.IExtension%601> uygulamasını türlerine göre almaya izin veren <xref:System.ServiceModel.IExtension%601> uygulamalarının bir koleksiyonudur.

Bu nedenle, <xref:System.ServiceModel.InstanceContext>genişletmek için <xref:System.ServiceModel.IExtension%601> arabirimini uygulamanız gerekir. Bu örnek projede, `CustomLeaseExtension` sınıfı bu uygulamayı içerir.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<xref:System.ServiceModel.IExtension%601> arabiriminin iki yöntemi vardır <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A>. Adları da bu iki yöntem, çalışma zamanı tarafından <xref:System.ServiceModel.InstanceContext> sınıfının bir örneğine ekler ve uzantıyı ayırır. Bu örnekte, uzantısının geçerli örneğine ait olan <xref:System.ServiceModel.InstanceContext> nesnesini izlemek için `Attach` yöntemi kullanılır.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

Ayrıca, genişletilmiş yaşam süresi desteğini sağlamak için gerekli uygulamayı uzantıya eklemeniz gerekir. Bu nedenle `ICustomLease` arabirimi istenen yöntemlerle bildirilmiştir ve `CustomLeaseExtension` sınıfında uygulanır.

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

WCF, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulamasında <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemini çağırdığında, bu çağrı `CustomLeaseExtension`<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemine yönlendirilir. Sonra, `CustomLeaseExtension` <xref:System.ServiceModel.InstanceContext> boşta olup olmadığını görmek için kendi özel durumunu denetler. Boşta ise `true`döndürür. Aksi halde, belirtilen miktarda genişletilmiş ömür için bir Zamanlayıcı başlatır.

```csharp
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

Zamanlayıcının `Elapsed` olayında, başka bir Temizleme döngüsünü başlatmak için dağıtıcıdaki geri çağırma işlevi çağırılır.

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

Boşta durumuna taşınan örnek için yeni bir ileti geldiğinde çalışan süreölçeri yenilemenin bir yolu yoktur.

Örnek, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemine yapılan çağrıları kesmeye ve bunları `CustomLeaseExtension`yönlendirmeye yönelik <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygular. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulama `CustomLifetimeLease` sınıfında bulunur. WCF hizmet örneğini serbest bırakmak üzere olduğunda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi çağrılır. Ancak, bu `ISharedSessionInstance` bir uygulamanın yalnızca bir örneği, ServiceBehavior 'in <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> koleksiyonunda bulunur. Bu, <xref:System.ServiceModel.InstanceContext> WCF 'nin <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemini denetleyip kapatmadığını bilmenin bir yolu olmadığı anlamına gelir. Bu nedenle, bu örnek <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoduna istekleri seri hale getirmek için iş parçacığı kilitleme kullanır.

> [!IMPORTANT]
> Serileştirme uygulamanızın performansını ciddi bir şekilde etkileyebileceğinden, iş parçacığı kilitleme kullanılması önerilen bir yaklaşım değildir.

Bir özel üye alanı, Boşta durumunu izlemek için `CustomLifetimeLease` sınıfında kullanılır ve <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi tarafından döndürülür. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi her çağrıldığında, `isIdle` alanı `false`olarak döndürülür ve sıfırlanır.  Dağıtıcıda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemini çağırdığından emin olmak için bu değerin `false` ayarlanması önemlidir.

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> yöntemi `false`döndürürse, dağıtıcı <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemini kullanarak bir geri çağırma işlevi kaydeder. Bu yöntem, serbest bırakılmakta olan <xref:System.ServiceModel.InstanceContext> bir başvuru alır. Bu nedenle, örnek kod `ICustomLease` türü uzantısını sorgulayabilir ve genişletilmiş durumdaki `ICustomLease.IsIdle` özelliğini denetleyebilir.

```csharp
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

`ICustomLease.IsIdle` özelliği denetlenmadan önce, `CustomLeaseExtension` bir süre boşta kaldığında dağıtıcıya bildirmesini sağlamak için gerekli olduğu için geri çağırma özelliğinin ayarlanması gerekir. `ICustomLease.IsIdle` `true`döndürürse `isIdle` özel üye `CustomLifetimeLease` yalnızca `true` olarak ayarlanır ve geri çağırma yöntemini çağırır. Kod bir kilit içerdiğinden, diğer iş parçacıkları bu özel üyenin değerini değiştiremezler. Dağıtıcı <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>bir sonraki sefer çağırdığında, `true` döndürür ve dağıtıcıda örneği serbest bırakmasına olanak tanır.

Artık özel uzantı için groundçalışmadığına göre, hizmet modeline bağlanmalıdır. `CustomLeaseExtension` uygulamasını <xref:System.ServiceModel.InstanceContext>bağlamak için WCF, <xref:System.ServiceModel.InstanceContext>önkurulumunu gerçekleştirmek için <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> arabirimi sağlar. Örnekte, `CustomLeaseInitializer` sınıfı bu arabirimi uygular ve tek yöntem başlatmasıyla <xref:System.ServiceModel.InstanceContext.Extensions%2A> koleksiyonuna bir `CustomLeaseExtension` örneği ekler. Bu yöntem, <xref:System.ServiceModel.InstanceContext>başlatılırken dağıtıcı tarafından çağırılır.

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Son olarak <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulama, <xref:System.ServiceModel.Description.IServiceBehavior> uygulamasını kullanarak hizmet modeline bağlanır. Bu uygulama `CustomLeaseTimeAttribute` sınıfına yerleştirilir ve ayrıca bu davranışı bir öznitelik olarak göstermek için <xref:System.Attribute> temel sınıfından türetilir.

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

Bu davranış örnek bir hizmet sınıfına, `CustomLeaseTime` özniteliğiyle birlikte ek olarak eklenebilir.

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için bir kerelik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
