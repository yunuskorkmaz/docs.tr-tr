---
title: Temel XAML yalnızca hizmeti
ms.date: 03/30/2017
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
ms.openlocfilehash: aa6b6ec6930ac90fe95b1cdfcd4cb027de8e5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`