---
title: Temel TransactionScope
ms.date: 03/30/2017
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
ms.openlocfilehash: b3c673040d40ca91d8ab4a79e847d61e6f507ed1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415429"
---
# <a name="basic-transactionscope"></a>Temel TransactionScope
Bu örnekte dört senaryo oluşur, çalışan iç içe gösteren <xref:System.Activities.Statements.TransactionScope> örnekleri. İlk senaryoda yazar bilgisi oluşturma olan 3 bir taraf etkinlik iç içe geçirme gösterilmektedir. Zaman aşımları nasıl uymaya ikinci ve üçüncü senaryolarını göstermek ve son senaryo gösterilmektedir <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> ayarı.  
  
## <a name="nesting-of-transactionscopeactivity"></a>İç içe geçmiş TransactionScopeActivity  
 İlk senaryo için iş akışı dizisi iki oluşur <xref:System.Activities.Statements.WriteLine> etkinlikleri ve <xref:System.Activities.Statements.TransactionScope>. Gövdesi <xref:System.Activities.Statements.TransactionScope> iki tane daha oluşan bir dizidir <xref:System.Activities.Statements.WriteLine> etkinlikler, işlem ve üçüncü bir yerel tanımlayıcısını yazdırır özel bir etkinlik taraf etkinlik. Üçüncü taraf etkinlik `TransactionScopeTest` içeren bir <xref:System.Activities.Statements.TransactionScope> olduğunu bilmesinin imkanı olsa da iş akışı yazar. Bu senaryoyu gösteren <xref:System.Activities.Statements.TransactionScope> etkinlikleri iç içe geçirilemez.  
  
## <a name="time-outs"></a>Zaman aşımları  
 İkinci senaryo için iş akışı, ilk neredeyse aynıdır. `TransactionScopeTest` İle değiştirilmiştir bir <xref:System.Activities.Statements.TransactionScope>. Gövdesi <xref:System.Activities.Statements.TransactionScope> 5 saniyelik gecikme ve işlem için zaman aşımı süresi iki saniye olarak ayarlanır. Dış için zaman aşımını <xref:System.Activities.Statements.TransactionScope> 10 saniye olarak ayarlanır. En küçük zaman aşımını kapsamında dikkate ve işlem zaman aşımına unutmayın.  
  
 Üçüncü senaryo için iş akışı, iki senaryo için neredeyse aynıdır. Delay etkinlik iç gövdesinden taşındı <xref:System.Activities.Statements.TransactionScope> hemen sonrasına dizideki dış gövdesi olan <xref:System.Activities.Statements.TransactionScope>. İşlem zaman aşımına hala ancak iki iç zaman aşımını saniye <xref:System.Activities.Statements.TransactionScope> artık geçerlidir. İşlem zaman aşımına uğrar, 10 saniyelik zaman dış <xref:System.Activities.Statements.TransactionScope> zaman aşımı aşıldı.  
  
## <a name="aborting-on-transaction-failure"></a>Hata durumunda işlem iptal ediliyor  
 Zaman aşımlarını almıştır dışında bu iş akışı senaryo üç benzer <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> özelliği. Unutmayın tüm iç alt öğelerini, Bayraklar, ayarla, dış eşleşmelidir <xref:System.Activities.Statements.TransactionScope>. Bu senaryoda, bunlar yapın ve iş akışı açıldığında bir özel durum oluşturulur.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  BasicTransactionScopeSample.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın veya seçin **Çözümü Derle** gelen **derleme** menüsü.  
  
3.  Derleme başarılı olana sonra F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Bunun yerine CTRL + F5 tuşlarına basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** hata ayıklama olmadan çalıştırmak için menü.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`