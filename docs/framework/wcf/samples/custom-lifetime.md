---
description: 'Daha fazla bilgi edinin: özel ömür'
title: Özel ömür
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 24845aaa20e60f92e2add568c81ab3d6502ebedf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732481"
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

Diğer örnek oluşturma modlarının aksine, paylaşılan örnek oluşturma modunun hizmet örneklerini serbest bırakma yöntemine özgü bir yolu vardır. Varsayılan olarak, tüm kanallar bir için kapatıldığında <xref:System.ServiceModel.InstanceContext> , WCF hizmeti çalışma zamanı hizmetin veya olarak yapılandırılmış olup olmadığını denetler ve bu <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerCall> <xref:System.ServiceModel.InstanceContextMode.PerSession> durumda örneği serbest bırakır ve kaynakları talep eder. Bir özel <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kullanılıyorsa, WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> örneği bırakmadan önce sağlayıcı uygulamasının yöntemini çağırır. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `true` Örneği serbest bırakıldığında, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> `Dispatcher` bir geri çağırma yöntemi kullanarak boşta durumuna bildirimde bulunmak için uygulama sorumludur. Bu, sağlayıcının yöntemi çağırarak yapılır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> .

Bu örnek, <xref:System.ServiceModel.InstanceContext> bir boşta kalma zaman aşımı ile 20 saniye serbest bırakmayı nasıl erteleyebileceğinizi gösterir.

## <a name="extending-the-instancecontext"></a>InstanceContext 'i genişletme

WCF 'de, <xref:System.ServiceModel.InstanceContext> hizmet örneği ve ile arasındaki bağlantıdır `Dispatcher` . WCF, genişletilebilir nesne düzenlerini kullanarak bu çalışma zamanı bileşenini yeni durum veya davranış ekleyerek genişletmenizi sağlar. Genişletilebilir nesne stili, mevcut çalışma zamanı sınıflarını yeni işlevlerle genişletmek ya da bir nesneye yeni durum özellikleri eklemek için WCF 'de kullanılır. Genişletilebilir nesne deseninin üç arabirimi vardır: <xref:System.ServiceModel.IExtensibleObject%601> , <xref:System.ServiceModel.IExtension%601> ve <xref:System.ServiceModel.IExtensionCollection%601> .

<xref:System.ServiceModel.IExtensibleObject%601>Arabirim, işlevlerini özelleştiren uzantılara izin vermek için nesneleri tarafından uygulanır.

<xref:System.ServiceModel.IExtension%601>Arabirim, türündeki sınıfların uzantıları olabilecek nesneler tarafından uygulanır `T` .

Son olarak, <xref:System.ServiceModel.IExtensionCollection%601> arabirim, <xref:System.ServiceModel.IExtension%601> <xref:System.ServiceModel.IExtension%601> kendi türlerine göre uygulamasının alınmasına izin veren bir uygulamalar koleksiyonudur.

Bu nedenle, öğesini genişletmek için <xref:System.ServiceModel.InstanceContext> arabirimini uygulamanız gerekir <xref:System.ServiceModel.IExtension%601> . Bu örnek projede, `CustomLeaseExtension` sınıfı bu uygulamayı içerir.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<xref:System.ServiceModel.IExtension%601>Arabirimin iki yöntemi vardır <xref:System.ServiceModel.IExtension%601.Attach%2A> <xref:System.ServiceModel.IExtension%601.Detach%2A> . Adları da bu iki yöntem, çalışma zamanı, uzantıyı bir sınıfın örneğine iliştirir ve ayrıldığında çağrılır <xref:System.ServiceModel.InstanceContext> . Bu örnekte, `Attach` yöntemi <xref:System.ServiceModel.InstanceContext> uzantının geçerli örneğine ait olan nesneyi izlemek için kullanılır.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

Ayrıca, genişletilmiş yaşam süresi desteğini sağlamak için gerekli uygulamayı uzantıya eklemeniz gerekir. Bu nedenle, `ICustomLease` arabirim istenen yöntemlerle bildirilmiştir ve `CustomLeaseExtension` sınıfında uygulanır.

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

WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> uygulamada yöntemi çağırdığında <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> , bu çağrı <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> öğesinin metoduna yönlendirilir `CustomLeaseExtension` . Sonra, `CustomLeaseExtension` öğesinin boşta olup olmadığını görmek için özel durumunu denetler <xref:System.ServiceModel.InstanceContext> . Boşta kalırsa, döndürür `true` . Aksi halde, belirtilen miktarda genişletilmiş ömür için bir Zamanlayıcı başlatır.

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

Zamanlayıcının `Elapsed` olayında, başka bir Temizleme döngüsünü başlatmak Için dağıtıcıdaki geri çağırma işlevi çağırılır.

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

Örnek, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> yöntemine yapılan çağrıları kesmeye <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> ve bunlara yönlendirmelerini uygular `CustomLeaseExtension` . <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>Uygulama `CustomLifetimeLease` sınıfında bulunur. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>WCF hizmet örneğini serbest bırakmak üzere olduğunda yöntem çağrılır. Ancak, bu, bir uygulamanın yalnızca bir örneği olan bir tek örnek olarak, `ISharedSessionInstance` ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> koleksiyonunun koleksiyonunda bulunur. Bu, <xref:System.ServiceModel.InstanceContext> WCF 'nin yöntemi denetleyip kapatılmadığını bilmenin bir yolu olmadığı anlamına gelir <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> . Bu nedenle, bu örnek metoduna istekleri seri hale getirmek için iş parçacığı kilitleme kullanır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> .

> [!IMPORTANT]
> Serileştirme uygulamanızın performansını ciddi bir şekilde etkileyebileceğinden, iş parçacığı kilitleme kullanılması önerilen bir yaklaşım değildir.

Bir özel üye alanı, `CustomLifetimeLease` Boşta durumunu izlemek için sınıfında kullanılır ve yöntemi tarafından döndürülür <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> . <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>Yöntemi her çağrıldığında, `isIdle` alan olarak döndürülür ve sıfırlanır `false` .  `false`Dağıtıcıda yöntemi çağırdığından emin olmak için bu değerin olarak ayarlanması gereklidir <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> .

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

<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>Yöntemi döndürürse `false` , dağıtıcı yöntemini kullanarak bir geri çağırma işlevi kaydeder <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> . Bu yöntem, <xref:System.ServiceModel.InstanceContext> serbest bırakılmakta olan öğesine bir başvuru alır. Bu nedenle, örnek kod `ICustomLease` tür uzantısını sorgulayabilir ve `ICustomLease.IsIdle` genişletilmiş durumdaki özelliği kontrol edebilir.

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

`ICustomLease.IsIdle`Özellik denetlenmadan önce, bu, dağıtıcıya boşta kaldığında bildirimde bulunması için gerekli olduğundan geri çağırma özelliği ayarlanmalıdır `CustomLeaseExtension` . `ICustomLease.IsIdle`Öğesini döndürürse `true` , `isIdle` özel üye ' ın `CustomLifetimeLease` öğesine ayarlanır `true` ve geri çağırma yöntemini çağırır. Kod bir kilit içerdiğinden, diğer iş parçacıkları bu özel üyenin değerini değiştiremezler. Dağıtıcısı bir sonraki sefer aradığında,, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> `true` Dispatcher örneğini serbest bırakmasına izin verir.

Artık özel uzantı için groundçalışmadığına göre, hizmet modeline bağlanmalıdır. `CustomLeaseExtension`Uygulamanızı öğesine bağlamak için <xref:System.ServiceModel.InstanceContext> WCF, ' nin önkurulumunu <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> gerçekleştirme arabirimini sağlar <xref:System.ServiceModel.InstanceContext> . Örnekte, `CustomLeaseInitializer` sınıfı bu arabirimi uygular ve `CustomLeaseExtension` <xref:System.ServiceModel.InstanceContext.Extensions%2A> tek yöntem başlatmasıyla koleksiyona bir örneği ekler. Bu yöntem, başlatılırken dağıtıcı tarafından çağırılır <xref:System.ServiceModel.InstanceContext> .

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Son olarak, uygulama, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulamayı kullanarak hizmet modeline bağlanır <xref:System.ServiceModel.Description.IServiceBehavior> . Bu uygulama `CustomLeaseTimeAttribute` sınıfına yerleştirilir ve ayrıca <xref:System.Attribute> Bu davranışı bir öznitelik olarak göstermek için temel sınıftan türetilir.

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

Bu davranış, özniteliğe ek olarak eklenerek örnek bir hizmet sınıfına eklenebilir `CustomLeaseTime` .

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

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
