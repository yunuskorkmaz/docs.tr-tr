---
title: Kapat ve Durdur seçeneklerini kullanarak WCF istemci kaynaklarını serbest bırakma
description: Dispose başarısız olabilir ve ağ başarısız olduğunda özel durum oluşturabilir. Bu, istenmeyen davranışa neden olabilir. Bunun yerine, ağ başarısız olduğunda istemci kaynaklarını serbest bırakmak için Kapat ve Iptal ' i kullanın.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 38861252a470f71a6fa88554e289344e2918d710
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715328"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>Ağ bağlantıları kesildiğinde yayın kaynaklarını güvenli bir şekilde kapat ve Iptal et

Bu örnek, yazılan bir istemci kullanılırken kaynakları temizlemek için `Close` ve `Abort` yöntemlerinin kullanımını gösterir. `using` deyimleri, ağ bağlantısı sağlam olmadığında özel durumlara neden olur. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır. Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, yazılı istemcilerle C# "Using" ifadesinin yanı sıra özel durumların ardından doğru şekilde temizlem kodu kullanırken oluşan yaygın sorunlardan ikisini gösterir.

C# "Using" ifadesinde `Dispose`() çağrısı oluşur. Bu, bir ağ hatası oluştuğunda özel durum oluşturabilecek `Close`() ile aynıdır. `Dispose`() çağrısı "Using" bloğunun kapatma küme ayracı içinde örtük olarak yapıldığından, bu özel durum kaynağının, kodu yazan ve kodu okuyan kişilerin fark etmeme olasılığı yüksektir. Bu, olası bir uygulama hataları kaynağını temsil eder.

`DemonstrateProblemUsingCanThrow` yönteminde gösterilen ilk sorun, kapatma küme ayracı bir özel durum yaratmakta ve kapatma küme ayracından sonraki kodun yürütülmemelidir:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

Using bloğunun içindeki hiçbir şey bir özel durum oluşturursa veya using bloğunun içindeki tüm özel durumlar yakalansa bile, kapatma küme ayracı içindeki örtük `Dispose`() çağrısı bir özel durum oluşturabileceğinden `Console.WriteLine` gerçekleşmeyebilir.

`DemonstrateProblemUsingCanThrowAndMask` yönteminde gösterilen ikinci sorun, kapanış küme ayracı bir özel durum oluşturan başka bir sorundur:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

`Dispose`() bir "Finally" bloğunda gerçekleştiği için, `Dispose`() başarısız olursa, `ApplicationException`, using bloğunun dışında hiçbir şekilde görülmez. Dış kodun `ApplicationException` gerçekleştiği zaman hakkında bilgi sahibi olması gerekiyorsa, "Using" yapısı bu özel durumu maskeleyerek soruna neden olabilir.

Son olarak, örnek, `DemonstrateCleanupWithExceptions`özel durumlar oluştuğunda doğru şekilde nasıl temizleyeceğinizi gösterir. Bu, hataları raporlamak ve `Abort`çağırmak için bir try/catch bloğu kullanır. İstemci çağrılarından özel durumları yakalama hakkında daha fazla ayrıntı için [Beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) örneğine bakın.

```csharp
try
{
    ...
    client.Close();
}
catch (CommunicationException e)
{
    ...
    client.Abort();
}
catch (TimeoutException e)
{
    ...
    client.Abort();
}
catch (Exception e)
{
    ...
    client.Abort();
    throw;
}
```

> [!NOTE]
> Using deyimleri ve ServiceHost: birçok Self-barındırma uygulaması bir hizmeti barındırmakla çok daha fazla yapılır ve ServiceHost. Close nadiren bir özel durum oluşturur, bu nedenle bu uygulamalar, using ifadesini ServiceHost ile güvenli bir şekilde kullanabilir. Ancak ServiceHost. Close 'un bir `CommunicationException`oluşturabildiğini unutmayın. bu nedenle, uygulamanız ServiceHost kapatıldıktan sonra devam ederse, using deyiminden kaçınmalı ve daha önce verilen kalıbı izlemelisiniz.

Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.

İstemci işlemi, her biri `Divide`çağırmayı deneyen üç senaryo çalıştırır. İlk senaryo `Dispose`() öğesinden bir özel durum nedeniyle atlanan kodu gösterir. İkinci senaryo, `Dispose`() ' den özel bir durum nedeniyle maskelenen önemli özel durumu gösterir. Üçüncü senaryoda doğru temizleme gösterilmektedir.

İstemci işlemindeki beklenen çıkış:

```console
=
= Demonstrating problem:  closing brace of using statement can throw.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating cleanup with Exceptions.
=
Calling client.Add(0.0, 0.0);
        client.Add(0.0, 0.0); returned 0
Calling client.Divide(0.0, 0.0);
Got System.ServiceModel.CommunicationException from Divide.

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
