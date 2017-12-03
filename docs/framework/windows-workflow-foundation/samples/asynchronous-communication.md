---
title: "Zaman uyumsuz iletişim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea2d705a38ddae1689d212bbd50196920fe73fe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="asynchronous-communication"></a>Zaman uyumsuz iletişim
Bu örnek gösterilmektedir nasıl iki farklı arasındaki iletişimi [!INCLUDE[wf](../../../../includes/wf-md.md)] Hizmetleri zaman uyumsuz olarak varsayılan olarak yapılır.  
  
## <a name="demonstrates"></a>Gösteriler  
 Zaman uyumsuz iletişim arasında [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Hizmetleri.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek göstermektedir nasıl arasındaki iletişimi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamaları yapılır zaman uyumsuz olarak .NET Framework tarafından sağlanan Mesajlaşma etkinlikleri kullanarak.  
  
 Bu örnek, aşağıdaki üç projeleri oluşur.  
  
 CreditCheckService  
 Bu hizmet, belirli bir kişinin kredi puanı veya edinmek için öğenin değerini alır ve kredi kişiye verilen olup olmadığını belirler.  
  
 RentalApprovalService  
 Bu hizmetin gerekli bazı alacak olan bir kişi bir uygulamayı alır. Bu hizmet zaman uyumsuz olarak iletişim kurar `CreditCheckService` kredi uygulama geçerli olup olmadığına karar vermek için.  
  
 İstemci  
 İstemci eş zamanlı olarak iletişim kurar `RentalApprovalService` kredi onaylanmış olup olmadığını bilmek.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Sağ **AsynchronousCommunication** çözümü ve select **özellikleri**.  
  
2.  İçinde **ortak özellikleri**seçin **başlangıç projesi**seçip **birden fazla başlangıç projesi**.  
  
3.  Taşıma **RentalApprovalService** listedeki ilk konumuna arkasından **CreditCheckService**, ardından **istemci**. Ayarlama **Başlat** üç projenin eylem.  
  
4.  Tıklatın **Tamam**, örneği çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
