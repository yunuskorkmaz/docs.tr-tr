---
title: Temel XAML tek hizmet
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: f4f296a97b9c3093874c5ec8e05023e84b0af44a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320639"
---
# <a name="basic-xaml-only-service"></a>Temel XAML tek hizmet
Bu örnek bir XAML yalnızca hizmetin nasıl oluşturulacağını gösterir. Senaryo, araba ilgili sorunlar için bir tanılama hizmetidir. Hizmet, bir dizi soru sorunu tanılamak için istemci isteyen iş akışı olarak uygulanır. İki tür hizmet tanılama sorunları vardır (araba başlatamaz veya çalışmıyor koşullandırma hava). İş Akışı Tasarımcısı istek/yanıt şablondan üç Basit Hizmet işlemleri kullanıma sunmak için kullanır. IIS sanal dizini oluşturarak IIS'de barındırılan hizmet ve Web.config dosyaları ve service1.xamlx sanal dizine kopyalamak, derlenmiş kod gereklidir. Varsayılan olarak bu örnek otomatik olarak gerekli dosyaların WCF ve WF örnekleri için kurulum yönergeleri izlediğinde oluşturulan sanal dizine kopyalar: [kerelik Kurulum yordamı için Windows Communication Foundation örnekleri](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Visual Studio 2010'da yapılandırıldığında.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi derleyin.  
  
2.  [Çözüm temel dizini] \Client\bin\debug içinde oluşturulan istemci uygulamasını çalıştırın.  
  
3.  Uygulama Seçenekleri yazdırır. bir seçenek seçer. Yanıt Evet veya Hayır bunları uygulama bazı sorular sorar (E/H anahtarları kullanarak). Hizmet bittiğinde sorunları tanılama, uygulama bir tanılama yazdırır.  
  
4.  Uygulama Seçenekleri döner. Başka bir sorunu tanılamak veya uygulamadan çıkın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`