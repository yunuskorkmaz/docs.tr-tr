---
title: Temel TransactionScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01d5d6f35ed9eaa64786d18c2477862594c546be
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`