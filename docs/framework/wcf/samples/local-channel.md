---
title: Yerel Kanal
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 2473704c751ad0ea2d2a00bf7f3ea43d6e39498f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501513"
---
# <a name="local-channel"></a>Yerel Kanal
Yerel kanal aynı uygulama etki alanı içinde iletişim için kullanılan bir Windows Communication Foundation (WCF) aktarım kanalıdır. Burada istemci ve hizmet aynı uygulama etki alanında çalışan ve tipik WCF kanalı yığınının (seri hale getirme ve seri durumdan çıkarma iletilerinin) ek yükünü kaçınılmalıdır senaryoları için kullanışlıdır.  
  
## <a name="demonstrates"></a>Gösteriler  
 Yerel Kanal  
  
## <a name="discussion"></a>Tartışma  
 Örnek iki proje dosyaları içerir:  
  
-   **LocalChannel**: geçerli uygulama etki alanı içinde yerel kanal programlı gösterimi. Bu projede gönderen bileşeni ileti bir bellek içi sıraya koyar ve alıcı bileşen alması iletiyi kuyruktan.  
  
-   **ClientAndService**: Bu proje bir hizmeti bir konsol uygulamasında barındırır ve aynı uygulama etki alanı içinde hizmetinden çağırmak için bir istemci çalıştırır.  
  
 Yerel kanal tasarım kanal yığını ve hızını artırmak için seri hale getirme işlemi atlanıyor. Yerel taşıma kanalı, bir kuyruk hizmeti için istemci hizmeti çağrıları taşıma ve istemciye geri dönüş değeri kullanılarak uygulanır. Parametreler ve dönüş değerleri serileştirme yerine örnek nesneleri kopyalar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Derleme ve LocalChannel çözümü çalıştırın.  
  
2.  Hizmet ana bilgisayarı başlatılır ve istemcinin yerel kanal kullanarak hizmetini çağırır. Hizmet arama sonuçlarını görüntülemek için bir konsol penceresi görünür.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
