---
title: Zaman Uyumsuz İletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: a9da04e2c6d3c131603211f53c54fd25dde8d338
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005595"
---
# <a name="asynchronous-communication"></a>Zaman Uyumsuz İletişim
Bu örnek, iki farklı Windows Workflow Foundation (WF) hizmetler arasındaki iletişimi varsayılan olarak zaman uyumsuz olarak nasıl yapılacağı gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Zaman uyumsuz iletişim arasında [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Hizmetleri.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, gösterir nasıl arasındaki iletişimi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamaları yapılır zaman uyumsuz olarak .NET Framework tarafından sağlanan ileti etkinlikleri kullanarak.  
  
 Bu örnek, aşağıdaki üç projeleri oluşur.  
  
 CreditCheckService  
 Bu hizmet, belirli bir kişinin kredi puan veya edinmek için öğenin değerini alır ve ardından kredi kişiye verilir karar verir.  
  
 RentalApprovalService  
 Bu hizmet, bir uygulama geçirilmesi gereken bazı alacak olan bir kişiden alır. Bu hizmet zaman uyumsuz olarak iletişim kurar `CreditCheckService` kredi başvurusunun geçerli olup olmadığına karar vermek için.  
  
 İstemci  
 İstemci eş zamanlı olarak iletişim kurar `RentalApprovalService` kredi onaylanmış olup olmadığını bilmek.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Sağ **AsynchronousCommunication** çözüm ve select **özellikleri**.  
  
2. İçinde **ortak özellikler**seçin **başlangıç projesi**seçip **birden fazla başlangıç projesi**.  
  
3. Taşıma **RentalApprovalService** ve ardından listedeki ilk konuma **CreditCheckService**çizgidir **istemci**. Ayarlama **Başlat** üç projenin tamamına eylem.  
  
4. Tıklayın **Tamam**, örneği çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
