---
title: "Gelişmiş İlkesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c83f4167ce1947b10f97e0cab5b5ddd2f8e00c76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-policy"></a>Gelişmiş İlkesi
Bu örnekte basit ilke örnek genişletir. Konut indirim ve iş indirim kuralları basit ilke örneğindeki ek olarak, çeşitli yeni kurallar eklenmiştir.  
  
 Yüksek değerli siparişleri büyük indirimi sağlayan bir yüksek değerli kuralı eklenir. Bir öncelik değeri verildiğinde'dan önceki iki kuralları indirim alanın üzerine ve hem konut üzerinden öncelik ve iş indirim kuralları.  
  
 Bir hesapla toplam kuralı Ayrıca, hangi indirim düzeyi temelinde toplam hesaplar eklenir. İş akışı etkinliğini tanımlanmış bir yöntem başvuru nasıl gibi başka eylemler kullanmayı gösterir. Bu kural, ayrıca, olacağından davranışı zincirleme dilediğiniz zaman indirim alan değişiklikleri hesaplanan gösterir. Ayrıca, yöntemi öznitelik atanıyor RuleWriteAttribute CalculateTotal yöntemi gösterilir. Bu, etkilenen kurallar yöntemi yürütülen her yeniden değerlendirilecek (ErrorTotalRule) neden olur.  
  
 Eklenen son kural hataları (Bu durumda, toplam 0'dan) algılarsa biridir. Bu durumda, ilke yürütme işlemi durduruldu.  
  
 Son olarak, `Console.Writeline` çağrıları, kural yürütme daha fazla görünürlük sağlamak için her bir kural eylemleri olarak eklenir, mümkün olmadığını da gösterirken statik yöntemler'na erişmek için türleri başvurulan. İzleme, yürütülen kurallara görünürlük almak için de kullanabilirsiniz.  
  
 Bu örnekte kullanılan kurallar şunlardır:  
  
 **ResidentialDiscountRule:**  
  
 Eğer sipariş değeri olarak > 500 ve CustomerType konut =  
  
 ARDINDAN indirim = % 5  
  
 **BusinessDiscountRule:**  
  
 Eğer sipariş değeri olarak > 10000 ve CustomerType iş =  
  
 ARDINDAN indirim = % 10  
  
 **HighValueDiscountRule:**  
  
 Eğer sipariş değeri olarak > 20000  
  
 ARDINDAN indirim % 15 =  
  
 **TotalRule:**  
  
 Eğer indirim > 0  
  
 ARDINDAN CalculateTotal (sipariş değeri olarak, indirim)  
  
 ELSE toplam sipariş değeri olarak =  
  
 **ErrorTotalRule:**  
  
 Eğer toplam \< 0  
  
 ARDINDAN hata = "ErrorTotalRule harekete"; Durdurma  
  
 Kural değerlendirmesi ve yürütme, ayrıca izleme ve izleme görülebilir.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  CTRL + F5'e basarak hata ayıklama olmadan çözümü çalıştırın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
-   Örnek için ana klasörü altında bulunan .exe dosyasını AdvancedPolicy\bin\debug klasöründe (veya örnek Visual Basic sürümü AdvancedPolicy \bin klasörünü) SDK komut istemi penceresinde çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Basit İlke](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
