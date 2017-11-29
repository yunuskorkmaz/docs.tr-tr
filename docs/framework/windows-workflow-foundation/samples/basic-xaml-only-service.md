---
title: "Temel XAML yalnızca hizmeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3fbf8a719647199439e2333ba5e26cbe51be3add
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-xaml-only-service"></a>Temel XAML yalnızca hizmeti
Bu örnek bir XAML yalnızca hizmetin nasıl oluşturulacağını gösterir. Senaryo bir araba ilgili sorunları tanılama hizmetidir. Hizmet, istemci bir dizi sorunu tanılamak için soru soran bir iş akışı olarak uygulanır. İki tür hizmet tanılama sorunları vardır (car başlatamaz veya çalışmıyor koşullandırma hava). İş Akışı Tasarımcısı'ndan istek/yanıt şablon üç Basit Hizmet işlemleri kullanıma sunmak için kullanır. IIS'de bir sanal dizin oluşturarak IIS'de barındırılan hizmet ve service1.xamlx ve Web.config dosyalarında sanal dizine kopyalama, derlenmiş kod gereklidir. Varsayılan olarak bu örnek otomatik olarak gerekli dosyaların WCF ve WF örnekleri için kurulum yönergeleri izlediğinizde oluşturulan sanal dizine kopyalar: [Windows Communication Foundation örnekleriiçinkerelikKurulumprosedürü](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Visual Studio 2010'da yapılandırıldığında.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi oluşturun.  
  
2.  [Çözüm temel dizin] \Client\bin\debug oluşturulan istemci uygulaması çalıştırın.  
  
3.  Uygulama Seçenekleri yazdırır bir seçenek seçer. Yanıt Evet veya Hayır bunları uygulama bazı sorular sorar (E/H anahtarları kullanarak). Hizmet tamamlandığında sorunlarını tanılama, uygulama tanılama yazdırır.  
  
4.  Uygulama geri seçenekleri gider. Başka bir sorunu tanılamak ya da uygulamadan çıkın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`  
  
## <a name="see-also"></a>Ayrıca Bkz.
