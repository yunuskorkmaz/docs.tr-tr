---
title: "Bağıntılı hesaplayıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53d96e090edabc65b7356497c3726d29e46c4ea7
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="correlated-calculator"></a>Bağıntılı hesaplayıcısı
Bu örnek ileti etkinlikleri kullanmak nasıl gösterir (<xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply>) iletisindeki bir parametre göre içerik tabanlı bağıntıyla Tasarımcısı'nda. Bu senaryoda paralel convoy hesaplayıcı işlemleridir. Bir örneği ve bir bağıntı (temel `CalculatorId`) ilk iletiyi iş akışı ve aynı sonraki ileti gönderildiğinde oluşturulan `CalculatorId` sıfırlama işlemi çağrılıncaya kadar bu örneğe gönderilir. İstemci hizmetiyle iletişim kurmak için kod tabanlı istemci proxy kullanan bir WPF uygulaması olarak uygulanır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Başlat [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yükseltilmiş izinler'de For.sln çözüm dosyasını açın.  
  
    1.  İçeren klasöre gidin [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Devenv.exe sağ tıklatıp **yönetici olarak çalıştır**.  
  
2.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CorrelatedCalculator.sln çözüm dosyasını açın.  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
4.  Hizmet projesinin çalıştırmak için CTRL + F5 tuşuna basın.  
  
5.  Hizmet, Çözüm Gezgini'nde, iletileri için hazır ve dinleme sonra istemci projesine sağ tıklayın ve çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`