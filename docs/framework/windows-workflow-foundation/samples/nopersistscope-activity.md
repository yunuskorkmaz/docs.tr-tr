---
title: NoPersistScope etkinliği
ms.date: 03/30/2017
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
ms.openlocfilehash: 6543756594b6734aec39bf22c5ab6215605341b1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46698262"
---
# <a name="nopersistscope-activity"></a>NoPersistScope etkinliği
Bu örnek, bir iş akışındaki serileştirilebilir olmayan ve tek kullanımlık bir durumu işlemek nasıl gösterir. Seri hale getirilemeyen durumu kalıcı hale getirmek iş akışlarını çalışmayın ve ayrıca önemli iş akışında kullanılan sonra temizlenmesi atılabilir nesneler için önemlidir.  
  
## <a name="demonstrates"></a>Gösteriler  
 `NoPersistScope` Özel Etkinlik ve Tasarımcısı.  
  
## <a name="using-the-nopersistzone-activity"></a>NoPersistZone etkinliğini kullanma  
 Örnek iş akışı çalıştığında, özel bir etkinlik olarak adlandırılan `CreateTextWriter` türünde bir nesne oluşturur <xref:System.IO.TextWriter> ve bir iş akışı değişkenine kaydeder. <xref:System.IO.TextWriter> olan bir <xref:System.IDisposable> nesne. Bu <xref:System.IO.TextWriter>, örnek çalıştığı, dizindeki ' out.txt' adlı bir dosyaya yazmak için yapılandırıldığı tarafından kullanılıyor bir <xref:System.Activities.Statements.WriteLine> etkinlik olarak yazdığınız konsolunda herhangi bir metin görüntülemektedir.  
  
 Yankı mantığı içinde çalışan bir `NoPersistScope` iş akışı kalıcı dan engelleyen etkinliği (kodu hangi Ayrıca bu örnek bir parçası). Yazarsanız `unload` konsolunda konak iş akışı örneği kalıcı dener ancak iş akışı içinde kaldığından bu işlem zaman aşımına bir `NoPersistScope`. İş akışı olarak adlandırılan özel bir etkinlik de yararlanır `Dispose` atmayı <xref:System.IO.TextWriter> nesne iş akışı tamamlandığında bunu kullanarak. `Dispose` Etkinliği içinde yerleştirilir <xref:System.Activities.Statements.TryCatch.Finally%2A> bloğu <xref:System.Activities.Statements.TryCatch> hangi etkinlik <xref:System.IO.TextWriter> değişken bildirimi, Try bloğunun yürütülmesi sırasında bir özel durum gerçekleşirse bile, çalıştığından emin olmak için.  
  
 Yazabilirsiniz `exit` iş akışı örneği tamamlamak ve programdan çıkın.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  NoPersistZone.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın veya seçin **Çözümü Derle** gelen **derleme** menüsü.  
  
3.  Derleme başarılı olana sonra F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menü alternatif olarak, CTRL + F5 tuşlarına basın veya seçin **hata ayıklama olmadan Başlat** gelen **Hata ayıklama** hata ayıklama olmadan çalıştırmak için menü.  
  
#### <a name="to-cleanup-optional"></a>Temizleme (isteğe bağlı)  
  
1.  SQL örneği Store kaldırmak için Cleanup.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`