---
title: Zaman uyumsuz iletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 9eafeab89aefb181ae016dc0219f9155d9bd2a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515166"
---
# <a name="asynchronous-communication"></a>Zaman uyumsuz iletişim
Bu örnekte, iki farklı Windows Workflow Foundation (WF) hizmeti arasındaki iletişimi varsayılan olarak zaman uyumsuz olarak nasıl yapılacağı gösterilmektedir.  
  
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
