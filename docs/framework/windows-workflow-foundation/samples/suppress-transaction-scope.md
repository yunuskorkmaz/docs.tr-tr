---
title: İşlem kapsamı gösterme
ms.date: 03/30/2017
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
ms.openlocfilehash: b38d168e7da4510b75ebeda7f4984c26fb68898d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518466"
---
# <a name="suppress-transaction-scope"></a>İşlem kapsamı gösterme
Örnek özel bir yazar gösterilmiştir `SuppressTransactionScope` ortam çalıştırma işlem varsa gizlemek için etkinlik.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Özel Etkinlik işlem akışını belirli bir senaryo için istenmeyen ise çıkışı başka bir hizmete aktarılan gelen bir işlem önlemek kullanışlıdır. İş akışı çalışma zamanı ortam işlemde gizleme için yerleşik destek sahip <xref:System.Activities.NativeActivity> için özel bir yazma işlemi gerçekleştirmek gerekli olduğu bu destek kullanabilir ancak sınıfı <xref:System.Activities.NativeActivity> Bu örnek bir gibi.  
  
 Senaryo üç bölümden oluşur. İlk olarak, bir <xref:System.Activities.Statements.TransactionScope> ortam hale bir çalışma zamanı işlem oluşturur. Bu işlem yerel ve dağıtılmış tanımlayıcıların yazdırır özel bir etkinlik tarafından doğrulanır. Uzak hizmet için ikinci bölümü başlamadan önce işlem sonra aktarılan. İş akışı sırasında ikinci bölümü, girer bir `SuppressTransactionScope` ve yeniden hareketi tanımlayıcıları yazdırma ve işlem akan işlemi yinelenir. Ancak, özel etkinlik bir ortam işlem bulamaz ve ileti akışı yapılan işlem hizmeti işlem içermiyor. Sonuç olarak, hizmet anlamına gelir istemci ve hizmet üzerinde dağıtılmış kimliği yazdırılan eşleşmeyen bir işlem oluşturur. Son bölümü sonra oluşan `SuppressTransactionScope` çıkar ve yeniden çalışma zamanı işlem başka bir ileti ilk iletinin tanımlayıcısı ile eşleşen dağıtılmış bir tanımlayıcı ile hizmetine tarafından doğrulanmış ortam olur.  
  
 Etkinlik türetilen <xref:System.Activities.NativeActivity> bir alt etkinlik zamanlama gerekir ve bir yürütme özelliği eklemek için. `SuppressTransactionScope` Sahip bir <xref:System.Activities.Variable> türü <xref:System.Activities.RuntimeTransactionHandle>, hangi kullanılmalıdır türü yerine bir örnek alanındaki <xref:System.Activities.RuntimeTransactionHandle> tanıtıcı başlatılmış olduğundan. `Variable<RuntimeTransactionHandle>` , Yalnızca dahili olarak kullanıldığından etkinliğe ilişkin meta verileri için bir uygulama değişkeni olarak eklenir.  
  
 Etkinlik çalıştırıldığında, önce bir gövde belirtilmiş olup olmadığını görmek için denetler ve varsa, ayarlar `SuppressTransaction` özelliği <xref:System.Activities.RuntimeTransactionHandle>. Özellik ayarlandıktan sonra yürütme özelliklerine eklenir ve ortam olur. Bir alt olan herhangi bir etkinlik buna `SuppressTransactionScope` özelliği görmeye ve bu nedenle çalışma zamanı işlem gizleme zorlar ve iç içe bir neden <xref:System.Activities.Statements.TransactionScope> bir özel durum için. Tanıtıcı gövdesi çalışacak şekilde zamanlanır yürütme özelliklerine eklendikten sonra.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  SuppressTransactionScope.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.  
  
3.  Derleme başarılı olduktan sonra çözüme sağ tıklayın ve seçin **başlangıç projelerini Ayarla**. İletişim kutusundan seçin **birden fazla başlangıç projesi** ve her iki projeleri için eylem olun **Başlat**.  
  
4.  F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Alternatif olarak, CTRL + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü hata ayıklama olmadan çalıştırma.  
  
    > [!NOTE]
    >  Sunucu, istemci başlatmadan önce çalışmalıdır. Hizmeti barındıran konsol penceresi çıktısı ne zaman başlatıldığını belirtir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`