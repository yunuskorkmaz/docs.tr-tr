---
title: Kalıcılık Katılımcıları
ms.date: 03/30/2017
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
ms.openlocfilehash: 18614962708eafa192d8163638fce2b8154d6106
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672659"
---
# <a name="persistence-participants"></a>Kalıcılık Katılımcıları
Kalıcılık Katılımcısı bir uygulama ana bilgisayarı tarafından tetiklenen bir Kalıcılık işlemi (kaydetme veya yük) katılabilir. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] İki soyut sınıf ile birlikte gelen **PersistenceParticipant** ve **PersistenceIOParticipant**, hangi Kalıcılık Katılımcısı oluşturma için kullanabilirsiniz. Kalıcılık Katılımcısı bu sınıflardan birine türetilen, ilgilenilen yöntemlerini uygular ve sonra sınıfa bir örneğini ekler <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> koleksiyonunda <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Uygulama konağı, bir iş akışı örneği kalıcı olduğunda bu tür iş akışı uzantılar için Ara ve uygun zamanlarda Kalıcılık katılımcıları uygun yöntemleri çağırmak olabilir.  
  
 Aşağıdaki listede, kalan (Kaydet) işlemi farklı aşamalarında Kalıcılık alt sistemi tarafından gerçekleştirilen görevleri açıklar. Kalıcılık katılımcıları üçüncü ve dördüncü aşamasında kullanılır. Katılımcı bir g/ç Katılımcısı (g/ç işlemlerinde da katıldığı bir Kalıcılık Katılımcısı) ise, katılımcı de altıncı aşamasında kullanılır.  
  
1. İş akışı durumu, yer işaretleri, eşlenen değişkenleri ve zaman damgası dahil olmak üzere yerleşik değerleri toplar.  
  
2. İş akışı örneği ile ilişkili Uzantı koleksiyonu eklenen tüm Kalıcılık katılımcıları toplar.  
  
3. Çağıran <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> tüm Kalıcılık katılımcıları tarafından uygulanan yöntem.  
  
4. Çağıran <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> tüm Kalıcılık katılımcıları tarafından uygulanan yöntem.  
  
5. Kalıcı veya iş akışı kalıcı depoya kaydedin.  
  
6. Çağıran <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> tüm g/ç Kalıcılık katılımcıları yöntemi. Katılımcı bir g/ç katılımcı değilse bu görev atlandı. Kalıcılık bölüm işlemsel ise, işlem Transaction.Current özelliğinde sağlanır.  
  
7. Tüm Kalıcılık katılımcıları tamamlanmasını bekler. Tüm katılımcıları kalıcı örnek verileri başarılı olursa, işlem taahhüt eder.  
  
 Kalıcılık Katılımcısı türetildiği **PersistenceParticipant** uygulayabilir ve sınıf **CollectValues** ve **MapValues** yöntemleri. Türetilen bir g/ç Kalıcılık Katılımcısı **PersistenceIOParticipant** uygulayabilir ve sınıf **BeginOnSave** uygulama yanı sıra yöntemi **CollectValues**ve **MapValues** yöntemleri.  
  
 Her aşama, sonraki aşamasına başlamadan önce tamamlanır. Örneğin, gelen değerleri toplanan **tüm** Kalıcılık katılımcıları ilk aşamasında. Ardından ilk aşamada toplanan tüm değerler tüm Kalıcılık Katılımcıları ikinci aşamasında eşleme için sağlanır. Ardından birinci ve İkinci aşamada eşlenen ve toplanan tüm değerler için kalıcı bir sağlayıcı üçüncü aşamada sağlanır ve benzeri.  
  
 Aşağıdaki listede, yükleme işlemi farklı aşamalarında Kalıcılık alt sistemi tarafından gerçekleştirilen görevleri açıklar. Kalıcılık katılımcıları dördüncü aşamasında kullanılır. Kalıcılık g/ç katılımcıları (g/ç işlemlerinde ayrıca katılmayı Kalıcılık katılımcıları), ayrıca üçüncü aşamada kullanılır.  
  
1. İş akışı örneği ile ilişkili Uzantı koleksiyonu eklenen tüm Kalıcılık katılımcıları toplar.  
  
2. İş akışını sürdürme deposundan yükler.  
  
3. Çağıran <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> tüm g/ç Kalıcılık Katılımcıları ve tamamlamak tüm Kalıcılık katılımcıları bekler. Kalıcılık bölüm işlemsel ise, işlem Transaction.Current sağlanır.  
  
4. İş akışı örneği sürdürme deposundan alınan verileri temel alan bellekte yükler.  
  
5. Çağıran <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> her Kalıcılık Katılımcısı üzerinde.  
  
 Kalıcılık Katılımcısı türetildiği **PersistenceParticipant** uygulayabilir ve sınıf **PublishValues** yöntemi. Türetilen bir g/ç Kalıcılık Katılımcısı **PersistenceIOParticipant** uygulayabilir ve sınıf **BeginOnLoad** uygulama yanı sıra yöntemi **PublishValues**yöntemi.  
  
 Bir iş akışı örneği yüklenirken kalıcı bir sağlayıcı bu örneği üzerinde bir kilit oluşturur. Bu örnek, bir çok düğümlü senaryosunda birden fazla konak tarafından yüklenen engeller. Kilitli bir iş akışı örneği yüklemeye çalışırsanız aşağıdaki gibi bir özel durum görürsünüz: Özel durum "System.ServiceModel.persistence.ınstancelockexception: İstenen işlemi tamamlayamadı çünkü kilitleme örneği için ' 00000000-0000-0000-0000-000000000000' alınmamış ". Aşağıdakilerden biri oluştuğunda, bu hataya neden olur:  
  
- Bir çok düğümlü senaryosunda örneği başka bir ana bilgisayar tarafından yüklenir.  Bu tür çakışmaları çözmek için birkaç farklı yolu vardır: yeniden deneme ve kilit sahibi olan düğüme işleme iletmek veya çalışmalarını kaydetmeleri için başka bir konak neden olacak yük zorla.  
  
- Tek düğümlü senaryo ve konak kilitlendi.  Ana bilgisayar başlatıldığında, kilit henüz süresi dolmadığından hala eski ana bilgisayar tarafından kilitli bir örnek yüklemek yeni ana bilgisayara yeniden (bir işlem geri dönüştürme veya yeni bir Kalıcılık sağlayıcı üreteci oluşturma) çalışır.  
  
- Tek düğümlü bir senaryo örneği, söz konusu noktada durduruldu ve farklı bir ana bilgisayar kimliği olan yeni bir Kalıcılık sağlayıcı örneği oluşturulur  
  
 Varsayılan değer olan 5 dakika kilit zaman aşımı değerine sahip, farklı bir zaman aşımı çağrılırken belirtebilirsiniz <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [Nasıl yapılır: Özel Kalıcılık Katılımcısı oluşturma](how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Depo Genişletilebilirliği](store-extensibility.md)
