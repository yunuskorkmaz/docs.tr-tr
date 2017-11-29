---
title: "Özel maaş örnek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3a9745c0cdd3a2d7050aed083d2eee5dfd4aaaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-compensation-sample"></a>Özel maaş örnek
Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Activities.Statements.CompensableActivity> ve özel maaş mantığını tanımlamak üzere kendi maaş işleyicisi. Bu örnekte Modellenen Kamyon kiralama Teşkilatı senaryodur.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Benzetimli adımlar şunlardır:  
  
1.  Kullanıcı isteklerini kiralama teklifleri için belirli bir tarih kamyon.  
  
2.  Üç kamyon şirketler kurulur ve üç tırnak sağlanır.  
  
3.  Kullanıcı bir kamyonu teklif seçer ve sipariş için kredi kartı ile devam eder.  
  
4.  Uygulama, diğer iki kamyon tırnak işareti iptal eder.  
  
5.  Uygulama iade iptali 10 gün olursa premium olmayan hesaplar için veya rezervasyon tarihi önce daha az bir hizmet ücret ister.  
  
6.  Uygulama Kamyon kiralama ücreti ister.  
  
7.  Uygulama rezervasyon tarihi veya müşteri ayırması iptal etmeye karar kadar hangisi önce gelirse bekler.  
  
8.  Müşteri ayırması iptal ederse <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> özel maaş mantığı göre aşağıdaki mantık çalışır:  
  
    1.  Müşterinin bir premium olmayan hesabı varsa ve 10 günden kısa bir süre önce rezervasyon tarihi sonra hizmet ücreti ise hala ücretlendirilir; Aksi takdirde, uygulama hizmeti ücret para iadeleri.  
  
    2.  Compensable etkinlikleri (kamyon sipariş + kamyon sipariş ücreti) kalanı ters sırada yürütülmesi dengelemek için varsayılan maaş mantığı göre çalıştırın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CustomCompensation.sln çözümü açın. \WF\Basic\Compensation\CustomCompensation dizininde bulunur.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`  
  
## <a name="see-also"></a>Ayrıca Bkz.
