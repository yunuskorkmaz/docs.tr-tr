---
title: İşlem kapsamını bastırma
ms.date: 03/30/2017
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
ms.openlocfilehash: 44814d66a4de4b3e72bb33eb46019eb1088ab040
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788045"
---
# <a name="suppress-transaction-scope"></a>İşlem kapsamını bastırma
Örnek özel bir yazma işlemi gösterilmektedir `SuppressTransactionScope` çalışma zamanı ortam işlem varsa bastırmak için etkinlik.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Özel Etkinlik, işlem akışını belirli bir senaryo için istenmeyen ise başka bir hizmete aktarılan çıkış gelen bir işlem önlemek yararlıdır. İş akışı çalışma zamanı içinde ortam işlem gizleme için yerleşik destek sunmaktadır <xref:System.Activities.NativeActivity> sınıfı, bu destek, özel bir yazma işlemi gerçekleştirmek gerekli olduğu için kullanabilir ancak <xref:System.Activities.NativeActivity> Bu örnek bir gibi.  
  
 Senaryo üç bölümden oluşur. İlk olarak, bir <xref:System.Activities.Statements.TransactionScope> ortam haline gelen çalışma zamanı bir işlem oluşturur. Bu işlemin yerel ve dağıtılmış tanımlayıcıları yazdıran özel bir etkinlik tarafından doğrulanır. İşlem uzak bir hizmete akıtılan ve ikinci bölümü başlamadan önce. İş akışı sırasında ikinci bölümü, girer bir `SuppressTransactionScope` ve yeniden işlem tanımlayıcıları yazdırma ve işlem akışı işlem yinelenir. Ancak, özel etkinlik bir ortam işlem bulmaz ve ileti akışı yapılan işlemler hizmeti işlem içermiyor. Sonuç olarak, hizmetin dağıtılmış kimliği istemci ve hizmeti gösterilip anlamına gelir eşleşmeyen bir işlem oluşturur. Sonra son bölümü oluşan `SuppressTransactionScope` çıkar ve yeniden çalışma zamanı işlem hizmetine ilk iletinin tanımlayıcısı eşleşen dağıtılmış bir tanımlayıcıya sahip başka bir ileti tarafından doğrulanmış ortam olur.  
  
 Etkinlik türetildiği <xref:System.Activities.NativeActivity> olduğundan, bir alt etkinlik zamanlama ve yürütme özelliğini eklemeniz gerekir. `SuppressTransactionScope` Sahip bir <xref:System.Activities.Variable> türü <xref:System.Activities.RuntimeTransactionHandle>, hangi kullanılmalıdır türü yerine bir örnek alanıyla <xref:System.Activities.RuntimeTransactionHandle> tanıtıcı başlatılması gerekir çünkü. `Variable<RuntimeTransactionHandle>` , Yalnızca dahili olarak kullanıldığından etkinliğe ilişkin meta verileri için bir uygulama değişken olarak eklenir.  
  
 Etkinlik yürütüldüğünde, öncelikle bir gövde belirtilmiş olup olmadığını görmek için denetler ve bu durumda, ayarlar `SuppressTransaction` özellikte <xref:System.Activities.RuntimeTransactionHandle>. Özelliği ayarlandıktan sonra yürütme özelliklerine eklenir ve ortam haline gelir. Bir alt öğesi olan herhangi bir etkinliği buna `SuppressTransactionScope` özelliği görebildiğine ve bu nedenle çalışma zamanı işlem gizlemeden zorunlu kılan ve iç içe bir neden <xref:System.Activities.Statements.TransactionScope> bir özel durum oluşturmak için. Tanıtıcı gövdesi çalışacak şekilde zamanlanırsa yürütme özellikleri eklendikten sonra.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  SuppressTransactionScope.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın veya seçin **Çözümü Derle** gelen **derleme** menüsü.  
  
3.  Derleme başarılı olana sonra çözümü sağ tıklatın ve seçin **başlangıç projelerini Ayarla**. İletişim kutusundan seçin **birden fazla başlangıç projesi** ve iki proje için bir eylem olduğundan emin olun **Başlat**.  
  
4.  F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü. Alternatif olarak, CTRL + F5 tuşlarına basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** hata ayıklama olmadan çalıştırmak için menü.  
  
    > [!NOTE]
    >  Sunucu, istemci başlatılmadan önce çalıştırılması gerekir. Hizmeti barındıran konsol penceresi çıktısı, ne zaman başladığını belirtir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`