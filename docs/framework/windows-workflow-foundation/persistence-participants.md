---
title: Kalıcılık Katılımcıları
ms.date: 03/30/2017
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
ms.openlocfilehash: 0bff6cc8fafb1832dc4d0e33b754fe3adb81dcf6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246114"
---
# <a name="persistence-participants"></a>Kalıcılık Katılımcıları

Kalıcılık Katılımcısı, bir uygulama ana bilgisayarı tarafından tetiklenen bir kalıcılık işlemine (kaydetme veya yükleme) katılabilir. , [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Bir Kalıcılık Katılımcısı oluşturmak için kullanabileceğiniz iki soyut sınıf ( **persistencekatılımcı** ve **Persistenceıopmakalenıpant**) ile birlikte gelir. Bir Kalıcılık Katılımcısı, bu sınıfların birinden türetilir, ilgilendiğiniz yöntemleri uygular ve sonra bir sınıfının bir örneğini <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> koleksiyonuna ekler <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Uygulama Konağı, bir iş akışı örneğini kalıcı hale getiren ve uygun zamanlarda Kalıcılık katılımcıları üzerinde uygun yöntemleri çağırdığınızda bu tür iş akışı uzantılarını arayabilir.  
  
 Aşağıdaki listede, devam eden (Kaydet) işleminin farklı aşamalarda Kalıcılık alt sistemi tarafından gerçekleştirilen görevler açıklanmaktadır. Kalıcılık katılımcıları, üçüncü ve dördüncü aşamalarda kullanılır. Katılımcı bir g/ç katılımcısıdır (g/ç işlemlerine da katılan bir Kalıcılık Katılımcısı), katılımcı de altıncı aşamada kullanılır.  
  
1. İş akışı durumu, yer işaretleri, eşlenmiş değişkenler ve zaman damgası dahil yerleşik değerleri toplar.  
  
2. İş akışı örneğiyle ilişkili uzantı koleksiyonuna eklenen tüm Kalıcılık katılımcılarını toplar.  
  
3. <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>Tüm Kalıcılık katılımcıları tarafından uygulanan yöntemi çağırır.  
  
4. <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A>Tüm Kalıcılık katılımcıları tarafından uygulanan yöntemi çağırır.  
  
5. İş akışını kalıcı hale getirin veya kalıcı depoya kaydedin.  
  
6. <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A>Tüm Kalıcılık g/ç katılımcıları üzerinde yöntemini çağırır. Katılımcı bir g/ç katılımcısı değilse, bu görev atlanır. Kalıcılık bölümü işlem ise, işlem Transaction. Current özelliğinde sağlanır.  
  
7. Tüm Kalıcılık katılımcılarının tamamlanmasını bekler. Tüm katılımcılar kalıcı örnek verilerinde başarılı olursa, işlemi kaydeder.  
  
 Bir Kalıcılık Katılımcısı, **persistencekatılımcı** sınıfından türetilir ve **CollectValues** ve **MapValues** yöntemlerini uygulayabilir. Kalıcılık g/ç katılımcısı, **Persistenceıopmakalenıpant** sınıfından türetilir ve **CollectValues** ve **MapValues** yöntemlerini uygulamaya ek olarak **BeginOnSave** metodunu uygulayabilir.  
  
 Her aşama, sonraki aşama başlamadan önce tamamlanır. Örneğin, ilk aşamadaki **Tüm** Kalıcılık katılımcılarının değerleri toplanır. Ardından ilk aşamada toplanan tüm değerler, eşleme için ikinci aşamadaki tüm Kalıcılık katılımcılarına sağlanır. Ardından ilk ve ikinci aşamada toplanan ve eşlenen tüm değerler, üçüncü aşamadaki Kalıcılık sağlayıcısına sağlanır ve bu şekilde devam eder.  
  
 Aşağıdaki listede, yük işleminin farklı aşamalarda Kalıcılık alt sistemi tarafından gerçekleştirilen görevler açıklanmaktadır. Kalıcılık katılımcıları dördüncü aşamada kullanılır. Kalıcılık g/ç katılımcıları (Ayrıca g/ç işlemlerine katılan Kalıcılık katılımcıları) üçüncü aşamada de kullanılır.  
  
1. İş akışı örneğiyle ilişkili uzantı koleksiyonuna eklenen tüm Kalıcılık katılımcılarını toplar.  
  
2. Kalıcılık deposundan iş akışını yükler.  
  
3. <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A>Tüm Kalıcılık g/ç katılımcıları üzerinde öğesini çağırır ve tüm Kalıcılık katılımcılarının tamamlanmasını bekler. Kalıcılık bölümü işlem halinde ise işlem Transaction. Current ' da sağlanır.  
  
4. Kalıcılık deposundan alınan verileri temel alarak, belleğe iş akışı örneğini yükler.  
  
5. <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A>Her bir Kalıcılık Katılımcısı üzerinde çağırır.  
  
 Bir Kalıcılık Katılımcısı, **persistencekatılımcı** sınıfından türetilir ve **PublishValues** metodunu uygulayabilir. Kalıcılık g/ç katılımcısı, **Persistenceıopmakalenıpant** sınıfından türetilir ve **PublishValues** metodunu uygulamaya ek olarak **BeginOnLoad** metodunu uygulayabilir.  
  
 Bir iş akışı örneği yüklenirken kalıcılık sağlayıcısı bu örnekte bir kilit oluşturur. Bu, örneğin çok düğümlü bir senaryoda birden çok konak tarafından yüklenmesini engeller. Kilitlenen bir iş akışı örneğini yüklemeye çalışırsanız, şunlar gibi bir özel durum görürsünüz: "System. ServiceModel. kalıcılık. InstanceLockException:" 00000000-0000-0000-0000-000000000000 "örneği için kilit alınamadığından istenen işlem tamamlanamadı. Aşağıdakilerden biri gerçekleştiğinde bu hata oluşur:  
  
- Çok düğümlü bir senaryoda, örnek başka bir ana bilgisayar tarafından yüklenir.  Bu çakışma türlerini çözmek için birkaç farklı yol vardır: işlemeyi, kilidi olan düğüme iletin ve yeniden deneyin ya da yükü zorlamak için, diğer konağın çalışmalarını kaydedememesine neden olacak.  
  
- Tek düğümlü bir senaryoda ve ana bilgisayar kilitlendi.  Konak yeniden başlatıldığında (bir işlem geri dönüşümü veya yeni bir kalıcılık sağlayıcısı fabrikası oluştururken), kilidin henüz geçerliliği tamamlanmadığından, yeni ana bilgisayar eski ana bilgisayar tarafından kilitlenen bir örneği yüklemeye çalışır.  
  
- Tek düğümlü bir senaryoda ve söz konusu örnek bir noktada durduruluyordu ve farklı bir ana bilgisayar KIMLIĞI olan yeni bir kalıcılık sağlayıcısı örneği oluşturulur.  
  
 Kilit zaman aşımı değeri varsayılan 5 dakikalık bir değere sahiptir, çağrılırken farklı bir zaman aşımı değeri belirtebilirsiniz <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A> .  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [Nasıl yapılır: Özel Kalıcılık Katılımcısı Oluşturma](how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Depo Genişletilebilirliği](store-extensibility.md)
