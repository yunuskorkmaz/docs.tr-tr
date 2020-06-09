---
title: Kapat ve Durdur seçeneklerini kullanarak WCF istemci kaynaklarını serbest bırakma
description: Dispose başarısız olabilir ve ağ başarısız olduğunda özel durum oluşturabilir. Bu, istenmeyen davranışa neden olabilir. Bunun yerine, ağ başarısız olduğunda istemci kaynaklarını serbest bırakmak için Kapat ve Iptal ' i kullanın.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: b338b760f461d7b773f43dd1f5e6dbce98f9e15a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599925"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a>Ağ bağlantıları kesildiğinde yayın kaynaklarını güvenli bir şekilde kapat ve Iptal et

Bu örnek, `Close` `Abort` türü belirlenmiş bir istemci kullanılırken kaynakları temizlemek için ve yöntemlerini gösterir. `using`Ağ bağlantısı sağlam olmadığında, ifade özel durumlara neden olur. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır. Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, C# "Using" ifadesinin yazılı istemcilerle birlikte kullanılması durumunda ortaya çıkan ve özel durumların ardından doğru şekilde temizliği olan kodun yanı sıra oluşan yaygın sorunlardan ikisini gösterir.

C# "Using" deyimleri () çağrısı ile sonuçlanır `Dispose` . Bu, `Close` () ile aynıdır ve bir ağ hatası oluştuğunda özel durumlar oluşturabilir. () Çağrısı, `Dispose` "Using" bloğunun kapatma küme ayracı içinde örtük olarak yapıldığından, bu özel durum kaynağının, kodu yazan ve kodu okuyan kişilerin fark etmeme olasılığı yüksektir. Bu, olası bir uygulama hataları kaynağını temsil eder.

Yönteminde gösterilen ilk sorun `DemonstrateProblemUsingCanThrow` , kapatma küme ayracı bir özel durum yaratmakta ve kapatma küme ayracından sonraki kodun yürütülmemelidir:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

Using bloğunun içindeki hiçbir şey bir özel durum oluşturursa veya using bloğunun içindeki tüm özel durumlar yakalansa bile, `Console.WriteLine` `Dispose` Kapanış küme ayracı içindeki örtük () çağrısı bir özel durum oluşturabileceğinden, bu durum gerçekleşmeyebilir.

Yönteminde gösterilen ikinci sorun `DemonstrateProblemUsingCanThrowAndMask` , kapanış küme ayracı bir özel durum oluşturan başka bir sorundur:

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

`Dispose`() Bir "Finally" bloğunda gerçekleştiğinden, `ApplicationException` () başarısız olursa,, (), using bloğunun dışında hiçbir şekilde görülmez `Dispose` . Dış kodun gerçekleştiği zaman hakkında bilmeleri gerekiyorsa `ApplicationException` , "Using" yapısı bu özel durumu maskeleyerek soruna neden olabilir.

Son olarak, örnek, içinde özel durumlar oluştuğunda nasıl doğru şekilde temizleyeceğinizi gösterir `DemonstrateCleanupWithExceptions` . Bu, hataları raporlamak ve çağırmak için bir try/catch bloğu kullanır `Abort` . İstemci çağrılarından özel durumları yakalama hakkında daha fazla ayrıntı için [Beklenen özel durumlar](expected-exceptions.md) örneğine bakın.

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
> Using deyimleri ve ServiceHost: birçok Self-barındırma uygulaması bir hizmeti barındırmakla çok daha fazla yapılır ve ServiceHost. Close nadiren bir özel durum oluşturur, bu nedenle bu uygulamalar, using ifadesini ServiceHost ile güvenli bir şekilde kullanabilir. Ancak ServiceHost. Close 'un bir oluşturup oluşturmadığını unutmayın. bu `CommunicationException` nedenle, uygulamanız ServiceHost kapatıldıktan sonra devam ederse, using deyiminden kaçınmalı ve daha önce verilen kalıbı izlemelisiniz.

Örneği çalıştırdığınızda, işlem yanıtları ve özel durumlar istemci konsol penceresinde görüntülenir.

İstemci işlemi her biri çağrı yapmaya çalışan üç senaryo çalıştırır `Divide` . İlk senaryo, () öğesinden bir özel durum nedeniyle atlanan kodu gösterir `Dispose` . İkinci senaryo, () öğesinden bir özel durum nedeniyle maskelenecek önemli bir özel durum gösterir `Dispose` . Üçüncü senaryoda doğru temizleme gösterilmektedir.

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

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
