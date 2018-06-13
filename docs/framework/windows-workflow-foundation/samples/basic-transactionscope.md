---
title: Temel TransactionScope
ms.date: 03/30/2017
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
ms.openlocfilehash: fe6877c4b2d72dc3d571740395fd4dc92ca8e99c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516808"
---
# <a name="basic-transactionscope"></a>Temel TransactionScope
Bu örnek dört senaryo oluşur çalıştırılan iç içe nasıl gösteren <xref:System.Activities.Statements.TransactionScope> örnekleri. İlk senaryoda Yazar yapım olanağıyla olan 3 bir taraf etkinlik iç içe geçme gösterir. Ne zaman aşımlarını dikkate ikinci ve üçüncü senaryolarını göstermek ve son senaryo gösterilmektedir <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> ayarı.  
  
## <a name="nesting-of-transactionscopeactivity"></a>TransactionScopeActivity iç içe geçmiş  
 İlk senaryo için iş akışını iki bir dizi oluşur <xref:System.Activities.Statements.WriteLine> etkinlikleri ve <xref:System.Activities.Statements.TransactionScope>. Gövdesini <xref:System.Activities.Statements.TransactionScope> daha fazla iki dizisidir <xref:System.Activities.Statements.WriteLine> etkinlikleri, işlem ve üçüncü bir yerel tanıtıcısı yazdırır özel bir aktivite taraf etkinlik. Üçüncü taraf etkinlik `TransactionScopeTest` içeren bir <xref:System.Activities.Statements.TransactionScope> bilerek hiçbir şekilde olsa da iş akışı yazar. Bu senaryo gösterilmektedir <xref:System.Activities.Statements.TransactionScope> etkinlikler iç içe geçirilemez.  
  
## <a name="time-outs"></a>Zaman aşımları  
 İkinci senaryo için iş akışını ilk neredeyse aynıdır. `TransactionScopeTest` İle değiştirilen bir <xref:System.Activities.Statements.TransactionScope>. Gövdesini <xref:System.Activities.Statements.TransactionScope> beş saniyelik gecikme ve işlem için zaman aşımı süresi iki saniye olarak ayarlanır. Dış için zaman aşımını <xref:System.Activities.Statements.TransactionScope> 10 saniye olarak ayarlayın. En küçük zaman aşımı kapsamında dikkate ve işlem zaman aşımına uğruyor unutmayın.  
  
 Üçüncü senaryo için iş akışını senaryo iki neredeyse aynıdır. Gecikme etkinlik iç gövdesinden taşındı <xref:System.Activities.Statements.TransactionScope> hemen sırası içinde sonra dış gövdesi olan <xref:System.Activities.Statements.TransactionScope>. İşlem zaman aşımına uğruyor hala ancak iki iç zaman aşımı ikinci <xref:System.Activities.Statements.TransactionScope> artık geçerli. İşlem zaman aşımına uğrar 10 saniyede zaman dış <xref:System.Activities.Statements.TransactionScope> zaman aşımı aşıldı.  
  
## <a name="aborting-on-transaction-failure"></a>İşlem hatası durduruluyor  
 Zaman aşımları almıştır dışında bu iş akışı senaryo üç benzer <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> özelliği. Unutmayın tüm iç alt bayrakları varsa ayarlayın, dış eşleşmelidir <xref:System.Activities.Statements.TransactionScope>. Bu senaryoda, bunlar yapın ve iş akışı açıldığında bir özel durum oluşur.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  BasicTransactionScopeSample.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.  
  
3.  Derleme başarılı olduktan sonra F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Alternatif olarak CTRL + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü hata ayıklama olmadan çalıştırma.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`