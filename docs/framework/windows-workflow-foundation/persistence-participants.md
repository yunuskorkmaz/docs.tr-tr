---
title: "Kalıcılık katılımcıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b85acf2e3c4d885988e92948481182b7cf8c32c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-participants"></a>Kalıcılık katılımcıları
Kalıcılık katılımcı bir uygulama ana bilgisayarı tarafından tetiklenen bir sürdürme işlemi (kaydetme veya yük) katılabilirsiniz. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İki soyut sınıflar ile birlikte gelen **PersistenceParticipant** ve **PersistenceIOParticipant**, hangi Kalıcılık katılımcı oluşturmak için kullanabilirsiniz. Kalıcılık katılımcı bu sınıfların birinden türetilen, ilgi yöntemlerini uygular ve sınıfının bir örneğini ekler <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> koleksiyonunda <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Uygulama ana bilgisayarı gibi iş akışı uzantıları için bir iş akışı örneği kalıcı olduğunda bakın ve uygun zamanlarda Kalıcılık katılımcıları uygun yöntemleri çağırma olabilir.  
  
 Aşağıdaki listede kalan (Kaydet) işlemi farklı aşamalarında Kalıcılık alt sistemi tarafından gerçekleştirilen görevleri açıklar. Kalıcılık katılımcıları üçüncü ve dördüncü aşamasında kullanılır. Katılımcı bir GÇ Katılımcısı (Ayrıca g/ç işlemlerinde katılan Kalıcılık katılımcı) ise, katılımcı de altıncı aşamasında kullanılır.  
  
1.  İş akışı durumu, yer işaretleri, eşlenen değişkenleri ve zaman damgası dahil olmak üzere yerleşik değerleri toplar.  
  
2.  İş akışı örneği ile ilişkili uzantı koleksiyonuna eklenen tüm Kalıcılık katılımcılar toplar.  
  
3.  Çağırır <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> tüm Kalıcılık katılımcıları tarafından uygulanan yöntem.  
  
4.  Çağırır <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> tüm Kalıcılık katılımcıları tarafından uygulanan yöntem.  
  
5.  Kalıcı hale getirmek veya iş akışını kalıcı depoya kaydedin.  
  
6.  Çağırır <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> tüm Kalıcılık GÇ katılımcının yöntemi. Katılımcı bir GÇ Katılımcısı değilse, bu görev atlanır. Kalıcılık bölüm işlemsel ise, işlem Transaction.Current özelliğinde sağlanır.  
  
7.  Tamamlamak Kalıcılık katılımcılarını bekler. İşlem, tüm katılımcılar kalıcı örnek verileri başarılı olursa, kaydeder.  
  
 Kalıcılık katılımcı türetilen **PersistenceParticipant** sınıfı ve uygulayabilir **CollectValues** ve **MapValues** yöntemleri. Kalıcılık GÇ katılımcı türetilen **PersistenceIOParticipant** sınıfı ve uygulayabilir **BeginOnSave** uygulama yanı sıra yöntemi **CollectValues**ve **MapValues** yöntemleri.  
  
 Her aşama, sonraki aşamasına başlamadan önce tamamlanır. Örneğin, gelen değerleri toplanan **tüm** Kalıcılık katılımcıları ilk aşamasında. Ardından ilk aşamasında toplanan tüm değerlerin ikinci aşaması eşleme için tüm Kalıcılık katılımcıları sağlanmaktadır. Ardından ilk ve İkinci aşamada eşlenen ve toplanan tüm değerleri Kalıcılık sağlayıcıya üçüncü aşamada sağlanır ve benzeri.  
  
 Aşağıdaki liste, yükleme işlemi farklı aşamalarında Kalıcılık alt sistemi tarafından gerçekleştirilen görevleri açıklar. Kalıcılık katılımcıları dördüncü aşamasında kullanılır. Kalıcılık GÇ katılımcıları (Ayrıca g/ç işlemlerinde katılmak Kalıcılık katılımcıları) üçüncü aşamada de kullanılır.  
  
1.  İş akışı örneği ile ilişkili uzantı koleksiyonuna eklenen tüm Kalıcılık katılımcılar toplar.  
  
2.  İş akışını sürdürme deposundan yükler.  
  
3.  Çağırır <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> tüm Kalıcılık GÇ Katılımcıları ve tamamlamak tüm Kalıcılık katılımcılar bekler. Kalıcılık bölüm işlemsel ise, işlem Transaction.Current içinde sağlanır.  
  
4.  İş akışı örneği Kalıcılık Mağazası'ndan alınan veriler temelinde bellekte yükler.  
  
5.  Çağırır <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> her Kalıcılık katılımcı üzerinde.  
  
 Kalıcılık katılımcı türetilen **PersistenceParticipant** sınıfı ve uygulayabilir **PublishValues** yöntemi. Kalıcılık GÇ katılımcı türetilen **PersistenceIOParticipant** sınıfı ve uygulayabilir **BeginOnLoad** uygulama yanı sıra yöntemi **PublishValues**yöntemi.  
  
 Bir iş akışı örneği yüklenirken Kalıcılık sağlayıcısı bu örneğinde bir kilit oluşturur. Bu örnek bir çok düğümlü senaryosunda birden çok ana bilgisayar tarafından yüklenmesini engeller. Kilitli bir iş akışı örneği yüklemeye çalışırsanız aşağıdaki gibi bir özel durum görürsünüz: özel durum "System.ServiceModel.persistence.ınstancelockexception: İstenen işlem tamamlanamadı kilidi örneği için ' 00000000-0000-0000-0000-000000000000' değil alınamadı ". Aşağıdakilerden biri oluştuğunda bu hataya neden olur:  
  
-   Bir çok düğümlü senaryosunda örneği başka bir ana bilgisayar tarafından yüklenir.  Bu tür çakışmaları çözümlemek için birkaç farklı yolu vardır: yeniden deneme ve kilit sahibi olan düğüme işleme iletmek veya işlerine kaydedemez başka bir ana neden olacak yük zorlayın.  
  
-   Bir tek düğümlü senaryo ve konak kilitlendi.  Ana bilgisayar başlatıldığında yeniden (işlem geri dönüştürme veya yeni bir Kalıcılık sağlayıcı fabrikası oluşturma) yeni ana bilgisayar olduğu kilidi henüz dolmadığından için eski ana bilgisayar tarafından hala kilitli örneğini yüklemeyi dener.  
  
-   Bir tek düğümlü senaryo ve örnek bir noktada söz konusu durduruldu ve farklı ana bilgisayar kimliği olan yeni bir Kalıcılık sağlayıcı örneği oluşturulur  
  
 Varsayılan değer olan 5 dakika kilit zaman aşımı değerine sahip, çağrılırken farklı zaman aşımı değeri belirleyebilirsiniz <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [Nasıl yapılır: Özel Kalıcılık Katılımcısı Oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Depo Genişletilebilirliği](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)
