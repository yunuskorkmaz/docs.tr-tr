---
title: Zaman Uyumsuz İletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142882"
---
# <a name="asynchronous-communication"></a>Zaman Uyumsuz İletişim
Bu örnek, iki farklı Windows İş Akışı Temeli (WF) hizmeti arasındaki iletişimin varsayılan olarak nasıl eşzamanlı olarak yapıldığını gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Hizmetler arasında [!INCLUDE[wf1](../../../../includes/wf1-md.md)] eşzamanlı iletişim.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, .NET [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Framework tarafından sağlanan ileti etkinlikleri kullanılarak uygulamalar arasındaki iletişimin nasıl eş senkronize bir şekilde yapıldığını gösterir.  
  
 Bu örnek aşağıdaki üç projeden oluşmaktadır.  
  
 CreditCheckService  
 Bu hizmet, belirli bir kişinin kredi puanını veya elde edilen maddenin değerini alır ve sonra kredinin kişiye verilip verilmeyeceğine karar verir.  
  
 Kiralama Onay Hizmeti  
 Bu hizmet, krediye ihtiyacı olan bir kişiden bir uygulama alır. Bu hizmet, kredi başvurusunun `CreditCheckService` geçerli olup olmadığına karar vermek için eş senkronize olarak iletişim kurar.  
  
 İstemci  
 İstemci, kredinin onaylanıp onaylanmadığını öğrenmek `RentalApprovalService` için senkronize olarak iletişim kurar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. **AsynchronousCommunication** çözümünü sağ tıklatın ve **Özellikler'i**seçin.  
  
2. **Ortak**Özellikler'de, **Başlangıç Projesi'ni**seçin ve **Birden Çok Başlangıç Projesi'ni**seçin.  
  
3. **RentalApprovalService** listede ilk pozisyona taşıyın, **CreditCheckService**takip , **Müşteri**izledi . Üç projede de **Başlat** eylemini ayarlayın.  
  
4. **Tamam'ı**tıklatın ve örneği çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
