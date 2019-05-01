---
title: Özel yaşam süresi
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: be6013d568e3625c5eac7e0c145db7df1c6917e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003172"
---
# <a name="custom-lifetime"></a>Özel yaşam süresi

Bu örnek nasıl paylaşılan WCF hizmet örneklerine yönelik özel yaşam süresi hizmetleri sağlamak için bir Windows Communication Foundation (WCF) uzantısı yazılacağını gösterir.

> [!NOTE]
> Bu örnek için Kurulum yordamı ve derleme yönergeleri bu makalenin sonunda yer alır.

## <a name="shared-instancing"></a>Paylaşılan örnek oluşturma

WCF hizmet örnekleriniz için birden çok örneklemesini modları sunar. Bu makalede ele alınan paylaşılan örneklemesini modu, bir hizmet örneği birden çok kanalda arasında paylaşmak için bir yol sağlar. İstemciler, bir Üreteç yöntemi hizmetinde başvurun ve iletişim başlatmak için yeni bir kanal oluşturmak. Aşağıdaki kod parçacığı bir istemci uygulamanın yeni bir kanal var olan bir hizmet örneğine nasıl oluşturduğunu gösterir:

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

Örneklemesini modlardan, paylaşılan örneklemesini modu hizmet örnekleri serbest benzersiz bir yolu yoktur. İçin tüm kanalları kapatıldığında varsayılan olarak bir <xref:System.ServiceModel.InstanceContext>, WCF Hizmeti çalışma zamanı olup olmadığını denetler. hizmet <xref:System.ServiceModel.InstanceContextMode> yapılandırılır <xref:System.ServiceModel.InstanceContextMode.PerCall> veya <xref:System.ServiceModel.InstanceContextMode.PerSession>ve bu nedenle örneği serbest bırakır ve kaynak talepleri. Özel durumunda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> olan kullanılan, WCF çağırır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> örneği serbest önce sağlayıcıyı uygulama yöntemi. Varsa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> döndürür `true` örneği, aksi takdirde serbest <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulamasıdır bildirmek için sorumlu `Dispatcher` boşta durumuna geri çağırma yöntemi kullanarak. Bu çağrılarak gerçekleştirilir <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> sağlayıcısının yöntemi.

Bu örnek nasıl serbest erteleyebilirsiniz gösterir <xref:System.ServiceModel.InstanceContext> 20 saniyelik bir boşta zaman aşımı ile.

## <a name="extending-the-instancecontext"></a>InstanceContext genişletme

Wcf'de, <xref:System.ServiceModel.InstanceContext> hizmet örneği arasında bağlantı ve `Dispatcher`. WCF yeni durum ya da davranışı, Genişletilebilir nesne düzeni'ni kullanarak ekleyerek bu çalışma zamanı bileşeni genişletmenizi sağlar. Genişletilebilir nesne düzeni WCF'de ya da var olan çalışma zamanı sınıflar yeni işlevlerle genişletmek veya bir nesne için yeni durum özellikler eklemek için kullanılır. Genişletilebilir nesne modelinde üç arabirimi vardır: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, ve <xref:System.ServiceModel.IExtensionCollection%601>.

<xref:System.ServiceModel.IExtensibleObject%601> Arabirimi işlevleriyle özelleştirme uzantılarına izin vermek için nesneler tarafından uygulanır.

<xref:System.ServiceModel.IExtension%601> Arabirimi sınıf türü uzantıları olabilir nesneleri tarafından uygulanan `T`.

Son olarak, <xref:System.ServiceModel.IExtensionCollection%601> arabirimidir koleksiyonu <xref:System.ServiceModel.IExtension%601> uygulaması almak için izin veren uygulamaları <xref:System.ServiceModel.IExtension%601> türüne göre.

Bu nedenle, genişletebilmek için <xref:System.ServiceModel.InstanceContext>, uygulamanız gereken <xref:System.ServiceModel.IExtension%601> arabirimi. Bu örnek projesinde `CustomLeaseExtension` sınıfı uygulaması içerir.

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<xref:System.ServiceModel.IExtension%601> Arabirimi iki yöntem vardır <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A>. Adlarını da ifade ettiği şekilde çalışma zamanı ekler ve uzantısı örneğine ayırır bu iki yöntem de çağrıldığında <xref:System.ServiceModel.InstanceContext> sınıfı. Bu örnekte `Attach` yöntemi izlemek için kullanılan <xref:System.ServiceModel.InstanceContext> uzantı geçerli örneğine ait nesne.

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

Ayrıca, gerekli uygulama genişletilmiş ömrü desteği sağlamak için uzantıya eklemeniz gerekir. Bu nedenle, `ICustomLease` arabirimi istenen yöntemleri ile bildirilir ve uygulanan `CustomLeaseExtension` sınıfı.

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

Ne zaman WCF çağırır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yönteminde <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulaması, bu çağrı için yönlendirilir <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi `CustomLeaseExtension`. Ardından, `CustomLeaseExtension` özel durumunu görmek için denetler olmadığını <xref:System.ServiceModel.InstanceContext> boştadır. Eğer boş ise, döndürür `true`. Aksi takdirde, genişletilmiş yaşam süresi belirtilen bir miktarı için bir süreölçer başlatır.

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

Zamanlayıcının içinde `Elapsed` olay dağıtıcısı içindeki geri arama işlevi başka bir temizleme döngüsü başlatmak için çağrılır.

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

Boşta durumuna taşınan örneği için yeni bir ileti geldiğinde çalışan Zamanlayıcı yenilemek için hiçbir yolu yoktur.

Örnek uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> çağrıları izlemesine <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi ve rota onları `CustomLeaseExtension`. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Uygulama kapsanıyorsa `CustomLifetimeLease` sınıfı. <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF hizmet örneği hakkında yayımlamayı olduğunda yöntemi çağrılır. Ancak, belirli bir yalnızca bir örneğini yoktur `ISharedSessionInstance` ServiceBehavior'ın uygulamasında <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> koleksiyonu. Bu biri olduğunu bilerek bir yolu yoktur anlamına gelir <xref:System.ServiceModel.InstanceContext> WCF denetler zaman kapalı <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi. Bu nedenle, bu örnek isteklerine seri hale getirmek için iş parçacığı kullanan <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi.

> [!IMPORTANT]
> Serileştirme uygulamanızın performansını önemli ölçüde etkileyebilir çünkü iş parçacığı kilitleme kullanmak önerilen bir yaklaşım değildir.

Özel üye alanı kullanılır `CustomLifetimeLease` boşta durumunu izlemek için sınıf ve tarafından döndürülen <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi. Her zaman <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi çağrıldığında `isIdle` alan döndürdü ve sıfırlama `false`.  Bu değeri ayarlamak için gerekli `false` dağıtıcı çağrıları emin olmak için <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemi.

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

Varsa <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> yöntemi döndürür `false`, dağıtıcı kullanarak bir geri çağırma işlevini kaydeder <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemi. Bu yöntem bir başvuru alır <xref:System.ServiceModel.InstanceContext> serbest bırakılıyor. Bu nedenle, örnek kod sorgulayabilirsiniz `ICustomLease` uzantısı yazın ve kontrol `ICustomLease.IsIdle` Genişletilmiş durum özelliğini.

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

Önce `ICustomLease.IsIdle` işaretli özelliği, geri çağırma özelliği için gerekli olduğundan ayarlanması gerekir `CustomLeaseExtension` boşta kaldığında göndereni bilgilendirmek için. Varsa `ICustomLease.IsIdle` döndürür `true`, `isIdle` özel üye ayarlamanız yeterlidir `CustomLifetimeLease` için `true` ve geri çağırma yöntemini çağırır. Kod bir kilit tuttuğunda olduğundan, diğer iş parçacıkları bu özel üye değerini değiştiremezsiniz. Ve dağıtıcı arar sonraki açışınızda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, döndürür `true` ve dağıtıcı örneği serbest olanak tanır.

Özel uzantı kavuşacak tamamlandı, hizmet modeli ölçekledikçe gerekmez. Bağlama için `CustomLeaseExtension` uygulamasına <xref:System.ServiceModel.InstanceContext>, WCF sağlar <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> , önyükleme gerçekleştirmek için arabirimi <xref:System.ServiceModel.InstanceContext>. Örnekte, `CustomLeaseInitializer` sınıfı bu arabirimi uygulayan ve bir örneğini ekler `CustomLeaseExtension` için <xref:System.ServiceModel.InstanceContext.Extensions%2A> koleksiyondan tek yöntemi başlatma. Bu yöntem tarafından dağıtıcısı başlatılırken çağrılır <xref:System.ServiceModel.InstanceContext>.

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 Son olarak <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulaması ölçekledikçe hizmet modeli kullanarak <xref:System.ServiceModel.Description.IServiceBehavior> uygulaması. Bu uygulama yerleştirilir `CustomLeaseTimeAttribute` sınıfı ve ayrıca türetilen <xref:System.Attribute> temel sınıfı, bu davranışı bir öznitelik olarak kullanıma sunmak için.

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

Bu davranışı için örnek bir hizmet sınıfı ile açıklama eklenebilir `CustomLeaseTime` özniteliği.

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.

### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1. Gerçekleştirdiğiniz emin olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](one-time-setup-procedure-for-the-wcf-samples.md).

2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](building-the-samples.md).

3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md).

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
