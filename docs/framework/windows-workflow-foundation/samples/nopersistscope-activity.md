---
title: "NoPersistScope etkinliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f0dae84428f079dc3efb0c7ee620fa8c6ff87a8f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="nopersistscope-activity"></a>NoPersistScope etkinliği
Bu örnek, bir iş akışındaki serileştirilebilir olmayan ve tek kullanımlık bir durumu işlemek gösterilmiştir. Seri hale getirilemeyen durumu devam ettirmek iş akışları çalışmayın ve ayrıca atılabilir nesnelerinin iş akışında kullanıldıktan sonra Temizlenen önemli olduğunu önemlidir.  
  
## <a name="demonstrates"></a>Gösteriler  
 `NoPersistScope`Özel Etkinlik ve Tasarımcısı.  
  
## <a name="using-the-nopersistzone-activity"></a>NoPersistZone etkinliğini kullanma  
 Örnek iş akışı çalıştığında, özel bir aktivite olarak adlandırılan `CreateTextWriter` türünde bir nesne oluşturur <xref:System.IO.TextWriter> ve bir iş akışı değişkenine kaydeder. <xref:System.IO.TextWriter>olan bir <xref:System.IDisposable> nesnesi. Bu <xref:System.IO.TextWriter>, örnek çalıştığı, dizindeki ' out.txt' adlı bir dosyaya yazmak için yapılandırıldığı tarafından kullanılıyor bir <xref:System.Activities.Statements.WriteLine> etkinlik olarak yazdığınız içinde konsolunda herhangi bir metin görüntülemektedir.  
  
 Echo mantığı içinde çalışan bir `NoPersistScope` iş akışı kalıcı olmasını önler (kodu hangi Ayrıca bu örnek bir parçası) etkinlik. Yazarsanız `unload` konsolunda ana iş akışı örneği kalıcı dener ancak iş akışı içinde kaldığından bu işlem zaman aşımına uğradı bir `NoPersistScope`. İş akışı da adlı özel bir aktivite kullanır `Dispose` silmek için <xref:System.IO.TextWriter> nesne iş akışı tamamlandığında kullanıyor. `Dispose` Etkinlik içinde yerleştirilir <xref:System.Activities.Statements.TryCatch.Finally%2A> , engellemek <xref:System.Activities.Statements.TryCatch> , etkinlik <xref:System.IO.TextWriter> değişkeni bildirilen, bir özel durum Try bloğunun yürütülmesi sırasında gerçekleşeceğini olsa bile bu çalıştığından emin olmak için.  
  
 Yazabilirsiniz `exit` iş akışı örneği tamamlamak ve programdan çıkın.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  NoPersistZone.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.  
  
3.  Derleme başarılı olduktan sonra F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menü alternatif olarak, CTRL + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **Hata ayıklama** menü hata ayıklama olmadan çalıştırma.  
  
#### <a name="to-cleanup-optional"></a>Temizleme (isteğe bağlı)  
  
1.  SQL örneği deposuna kaldırmak için Cleanup.cmd çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`