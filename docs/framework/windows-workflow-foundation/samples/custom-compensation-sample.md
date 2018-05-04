---
title: Özel maaş örnek
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c4d7219a2f16091d1997de6186312cce5ece0bd1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`