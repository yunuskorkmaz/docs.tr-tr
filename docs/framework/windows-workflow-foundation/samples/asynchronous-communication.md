---
title: Zaman Uyumsuz İletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 28b325a6bd870282577a2989b616628d52262deb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711855"
---
# <a name="asynchronous-communication"></a>Zaman Uyumsuz İletişim
Bu örnek, iki farklı Windows Workflow Foundation (WF) hizmeti arasındaki iletişimin zaman uyumsuz olarak varsayılan olarak nasıl yapıldığını gösterir.  
  
## <a name="demonstrates"></a>Gösterir  
 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] hizmetleri arasında zaman uyumsuz iletişim.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamalar arasındaki iletişimin, .NET Framework tarafından sunulan mesajlaşma etkinliklerini kullanarak zaman uyumsuz olarak nasıl yapılacağını gösterir.  
  
 Bu örnek, aşağıdaki üç projeden oluşur.  
  
 CreditCheckService  
 Bu hizmet belirli bir kişinin kredi Puanını veya alınacak öğenin değerini alır ve ardından kredinin kişiye verilip verilmeyeceğine karar verir.  
  
 RentalApprovalService  
 Bu hizmet, bazı kredilerin olması gereken bir kişiden uygulama alır. Bu hizmet, kredi uygulamasının geçerli olup olmadığına karar vermek için `CreditCheckService` ile zaman uyumsuz olarak iletişim kurar.  
  
 İstemci  
 İstemci, kredinin onaylanıp onaylanmadığını bildirmek için `RentalApprovalService` ile eşzamanlı olarak iletişim kurar.  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
