---
title: Zaman Uyumsuz İletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: b5cf788ce4587dacb5a7642e25cb1b5b1e6f3e3c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044360"
---
# <a name="asynchronous-communication"></a>Zaman Uyumsuz İletişim
Bu örnek, iki farklı Windows Workflow Foundation (WF) hizmeti arasındaki iletişimin zaman uyumsuz olarak varsayılan olarak nasıl yapıldığını gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Hizmetler arasında [!INCLUDE[wf1](../../../../includes/wf1-md.md)] zaman uyumsuz iletişim.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, .NET Framework tarafından sunulan mesajlaşma [!INCLUDE[wf1](../../../../includes/wf1-md.md)] etkinliklerini kullanarak uygulamalar arasındaki iletişimin zaman uyumsuz olarak nasıl yapılacağını gösterir.  
  
 Bu örnek, aşağıdaki üç projeden oluşur.  
  
 CreditCheckService  
 Bu hizmet belirli bir kişinin kredi Puanını veya alınacak öğenin değerini alır ve ardından kredinin kişiye verilip verilmeyeceğine karar verir.  
  
 RentalApprovalService  
 Bu hizmet, bazı kredilerin olması gereken bir kişiden uygulama alır. Bu hizmet, `CreditCheckService` kredi uygulamasının geçerli olup olmadığına karar vermek için ile zaman uyumsuz olarak iletişim kurar.  
  
 İstemci  
 İstemci, `RentalApprovalService` kredinin onaylanıp onaylanmadığını bildirmek için ile eşzamanlı olarak iletişim kurar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. **AsynchronousCommunication** çözümüne sağ tıklayın ve **Özellikler**' i seçin.  
  
2. **Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve **birden çok başlangıç**projesi ' ni seçin.  
  
3. **RentalApprovalService** ' i listedeki ilk konuma, ardından **CreditCheckService**ve ardından **Client**' a taşıyın. Her üç projede de **Başlangıç** eylemini ayarlayın.  
  
4. **Tamam**' a tıklayın ve örneği çalıştırmak için F5 ' e basın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
