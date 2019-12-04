---
title: Yerel Kanal
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714893"
---
# <a name="local-channel"></a>Yerel Kanal
Yerel kanal, aynı uygulama etki alanı içinde iletişim için kullanılan bir Windows Communication Foundation (WCF) aktarım kanaldır. Bu, istemcinin ve hizmetin aynı uygulama etki alanında çalıştığı senaryolarda ve tipik WCF kanal yığınının (iletilerin serileştirilmesi ve serisini kaldırma) önkullanılması kaçınılmalıdır.  
  
## <a name="demonstrates"></a>Gösterir  
 Yerel Kanal  
  
## <a name="discussion"></a>Tartışma  
 Örnek iki proje dosyasından oluşur:  
  
- **LocalChannel**: geçerli uygulama etki alanı içindeki yerel kanalın programlı gösterimi. Bu projede, gönderme bileşeni iletiyi bellek içi kuyruğa koyar ve alıcı bileşen iletiyi alacak şekilde kuyruğa alır.  
  
- **ClientAndService**: Bu proje bir konsol uygulamasında bir hizmet barındırır ve sonra aynı uygulama etki alanının içinden hizmeti çağırmak için bir istemci çalıştırır.  
  
 Yerel kanal tasarımı, hızı artırmak için hem kanal yığınını hem de serileştirme işlemini atlar. Yerel aktarım kanalı, hizmet çağrılarını istemciden hizmete aktarmak ve değeri istemciye geri döndürmek için bir kuyruk kullanılarak uygulanır. Parametreleri ve dönüş değerlerini serileştirmek yerine, örnek nesneleri kopyalar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. LocalChannel çözümünü derleyin ve çalıştırın.  
  
2. Hizmet ana bilgisayarı başlatılır ve istemci yerel kanalı kullanarak hizmeti çağırır. Hizmet çağrısının sonuçlarını görüntüleyen bir konsol penceresi görünür.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
