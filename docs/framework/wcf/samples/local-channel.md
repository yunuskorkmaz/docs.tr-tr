---
title: Yerel Kanal
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 11f3e4fe07ffa285f72ba8fd92224a3ba78d238b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656030"
---
# <a name="local-channel"></a>Yerel Kanal
Yerel kanal aynı uygulama etki alanı içinde iletişim kurmak için kullanılan bir Windows Communication Foundation (WCF) aktarım kanalıdır. Burada aynı uygulama etki alanında çalışan istemci ve hizmet ve ek yükü tipik WCF kanalı yığınının (seri hale getirme ve seri durumundan çıkarma iletilerinin) kaçınılmalıdır senaryoları için kullanışlıdır.  
  
## <a name="demonstrates"></a>Gösteriler  
 Yerel Kanal  
  
## <a name="discussion"></a>Tartışma  
 Örnek, iki proje dosyaları içerir:  
  
- **LocalChannel**: Yerel kanal geçerli uygulama etki alanı içinde programlı gösterimi. Bu projede gönderen bileşeni bellek içi kuyruğu ileti yerleştirir ve alıcı bileşen alması iletiyi kuyruktan.  
  
- **ClientAndService**: Bu proje bir hizmeti bir konsol uygulamasında barındırır ve aynı uygulama etki alanı içinde hizmetini çağırmak için bir istemci çalıştırır.  
  
 Yerel kanal tasarım kanal yığını hem hızını artırmak için seri hale getirme işlemi atlanıyor. Yerel taşıma kanalının hizmet çağrıları istemciden hizmete taşımayı ve istemciye geri dönüş değeri için bir kuyruk kullanma uygulanır. Örnek parametreler ve dönüş değerleri serileştirme yerine, nesneleri kopyalar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Derleme ve LocalChannel çözümü çalıştırın.  
  
2. Hizmet ana bilgisayarı başlatılır ve istemcinin yerel kanal'ı kullanarak hizmeti çağırır. Hizmet arama sonuçlarını görüntülemek için bir konsol penceresi görünür.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
