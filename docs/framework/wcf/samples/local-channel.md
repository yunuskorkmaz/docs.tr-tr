---
title: Yerel Kanal
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144513"
---
# <a name="local-channel"></a>Yerel Kanal
Yerel Kanal, aynı uygulama etki alanı içinde iletişim için kullanılan bir Windows Communication Foundation (WCF) aktarım kanalıdır. Bu, istemci ve hizmetin aynı uygulama etki alanında çalıştığı ve tipik WCF kanal yığınının (iletilerin serileştirme ve deserialization) ek yükünden kaçınılması gereken senaryolar için yararlıdır.  
  
## <a name="demonstrates"></a>Gösteriler  
 Yerel Kanal  
  
## <a name="discussion"></a>Tartışma  
 Örnek iki proje dosyasından oluşur:  
  
- **LocalChannel**: Yerel kanalın geçerli uygulama etki alanı içinde programlı gösterimi. Bu projede, gönderen bileşen iletiyi bellek içi sıraya yerleştirir ve alıcı bileşen iletiyi almak için sırayı ayırır.  
  
- **ClientAndService**: Bu proje bir konsol uygulamasında bir hizmeti barındırır ve ardından aynı uygulama etki alanı içinden hizmeti aramak için bir istemci çalıştırır.  
  
 Yerel kanal tasarımı, hızı artırmak için hem kanal yığınını hem de serileştirme işlemini atlar. Yerel aktarım kanalı, istemciden hizmet çağrılarını hizmete taşımak ve değeri istemciye geri döndürmek için bir sıra kullanılarak uygulanır. Örnek, parametreleri ve döndürme değerlerini serihale getirmek yerine nesneleri kopyalar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. LocalChannel çözümlerini oluşturun ve çalıştırın.  
  
2. Hizmet ana bilgisayarı başlatılır ve istemci yerel kanalı kullanarak hizmeti çağırır. Hizmet çağrısının sonuçlarını görüntülemek için bir konsol penceresi görüntülenir.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
