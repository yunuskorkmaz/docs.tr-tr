---
description: 'Daha fazla bilgi edinin: yerel kanal'
title: Yerel Kanal
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: a580abc1e8dcd89c40c9fdc02001deb094eb0b05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631755"
---
# <a name="local-channel"></a>Yerel Kanal

Yerel kanal, aynı uygulama etki alanı içinde iletişim için kullanılan bir Windows Communication Foundation (WCF) aktarım kanaldır. Bu, istemcinin ve hizmetin aynı uygulama etki alanında çalıştığı senaryolarda ve tipik WCF kanal yığınının (iletilerin serileştirilmesi ve serisini kaldırma) önkullanılması kaçınılmalıdır.  
  
## <a name="demonstrates"></a>Gösteriler  

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
