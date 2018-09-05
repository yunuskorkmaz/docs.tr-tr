---
title: Gelişmiş ilke
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: becdc28affd877239474d6f0f007a480297bccb8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672846"
---
# <a name="advanced-policy"></a>Gelişmiş ilke
Bu örnek, basit ilke örneği genişletir. Konut indirim ve iş indirim basit ilke örneği kurallarından ek olarak, birçok yeni kuralı eklendi.  
  
 Yüksek değerli siparişlerini büyük indirimi sağlayan bir yüksek değerli kuralı eklenir. Öncelik değeri verilir değerinden önceki iki kuralları indirim alanın üzerine ve her iki konut üzerinde önceliği ve iş indirim kuralları alır.  
  
 Calculate toplam kural da eklenir, indirim düzeyine dayalı toplam hesaplar. Bu, iş akışı etkinlikte tanımlanmış bir yöntem yapmayı yanı sıra başka eylemler kullanmayı gösterir. Bu kural, ayrıca olacağından, bu davranışı zincirleme dilediğiniz zaman değerlendirilen indirim alan değişiklikleri gösterir. Ayrıca, yöntemi öznitelik atanıyor RuleWriteAttribute CalculateTotal yöntemi gösterilir. Bu, etkilenen kurallar (yöntemi yürütülen her yeniden değerlendirilecek ErrorTotalRule) neden olur.  
  
 Eklenen son kuralı (Bu durumda, toplam 0'dan) hataları tespit biridir. Bu meydana gelirse, ilke yürütme durdurulur.  
  
 Son olarak, `Console.Writeline` çağrıları, kural yürütme daha fazla görünürlük sağlamak için her bir kural olarak eklenir, mümkün olduğunu da gösterirken statik yöntemler erişmeye türleri başvurulan. İzleme, yürütülen kurallara görünürlük elde etmek için de kullanabilirsiniz.  
  
 Bu örnekte kullanılan kurallar şunlardır:  
  
 **ResidentialDiscountRule:**  
  
 Eğer sipariş değeri olarak > 500 ve CustomerType konut =  
  
 ARDINDAN indirim = % 5  
  
 **BusinessDiscountRule:**  
  
 Eğer sipariş değeri olarak > 10000 ve CustomerType iş =  
  
 ARDINDAN indirim % 10 =  
  
 **HighValueDiscountRule:**  
  
 Eğer sipariş değeri olarak > 20000  
  
 ARDINDAN indirim % 15 =  
  
 **TotalRule:**  
  
 Eğer indirim > 0  
  
 ARDINDAN CalculateTotal (sipariş değeri olarak, indirim)  
  
 BAŞKA toplam sipariş değeri olarak =  
  
 **ErrorTotalRule:**  
  
 Eğer toplam \< 0  
  
 ARDINDAN, hata = "ErrorTotalRule harekete"; Durdurma  
  
 Kural değerlendirmesi ve yürütme, ayrıca izleme ve izleme görülebilir.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  CTRL + F5 tuşlarına basarak hata ayıklama olmadan çözümü çalıştırın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
-   SDK komut istemi penceresinde, örnek için ana klasörü altında bulunan .exe dosyasını AdvancedPolicy\bin\debug klasöre (veya Visual Basic sürümünü AdvancedPolicy \bin klasörünü) çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Basit İlke](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
