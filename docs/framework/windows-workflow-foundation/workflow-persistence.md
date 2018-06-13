---
title: İş akışı kalıcılığı
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: 8baae818db114567804d3796192249d6738fbb17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520087"
---
# <a name="workflow-persistence"></a>İş akışı kalıcılığı
İş akışı Kalıcılık dayanıklı yakalama bir iş akışı örneğinin durumu, işlem veya bilgisayar bilgilerinin bağımsız olur. Bu sistem hatası durumunda iş akışı örneği için iyi bilinen bir kurtarma noktası sağlamak üzere veya etkin olarak iş yapmamanın kaldırma iş akışı örnekleri tarafından bellek korumak için ya da iş akışı örneği çalışma durumu bir düğümden diğerine taşımak için gerçekleştirilir bir sunucu grubundaki düğümü.  
  
 İşlem çeviklik, ölçeklenebilirlik, Kurtarma hatası karşısında ve bellek daha verimli bir şekilde yönetme becerisini kalıcılığını etkinleştirir. Kalıcılık işlemi Kalıcılık noktasını, kaydedilecek veri toplama ve son olarak verilerin kalıcı bir sağlayıcı için gerçek depolama temsilci kimliğini içerir.  
  
 Bir iş akışı kalıcılığını etkinleştirmek için bir örnek depolama ile ilişkilendirmeniz gerekir **WorkflowApplication** veya **WorkflowServiceHost** bölümünde belirtildiği gibi [nasıl yapılır: kalıcılığı etkinleştir İş akışları ve iş akışı Hizmetleri](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md). **WorkflowApplication** ve **WorkflowServiceHost** Kalıcılık deposu ve iş akışı örneği yükleniyor kalıcı iş akışı örneği etkinleştirmek için onlarla ilişkili örnek deposuna kullanın Kalıcılık store içinde depolanan iş akışı örneği verileri temel bellek.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Birlikte **SqlWorkflowInstanceStore** verileri ve iş akışı örneği bir SQL Server 2005 veya SQL Server 2008 veritabanı içine hakkındaki meta verileri kalıcılığı sağlayan sınıf. Bkz: [SQL iş akışı örneği deposuna](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) daha fazla ayrıntı için.  
  
 Depolamak ve iş akışı örneği ile ilgili bilgilerin yanı sıra, uygulamaya özgü verileri yüklemek için genişletme Kalıcılık katılımcıları oluşturabilirsiniz <xref:System.Activities.Persistence.PersistenceParticipant> sınıfı. Kalıcı depoya belleğe örneği Mağazası'ndan veri yüklemeye ve ilave bir mantık Kalıcılık işlem altında gerçekleştirmek için özel seri hale getirilebilir veri kaydetmek için Kalıcılık işlemindeki Kalıcılık katılımcı katılır. Daha fazla bilgi için bkz: [Kalıcılık katılımcıları](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).  
  
 Windows Server App Fabric kalıcılığı yapılandırma işlemini basitleştirir. Daha fazla bilgi için bkz: [Windows Server App Fabric ile kalıcılığı kavramları](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Örtük Kalıcılık noktaları  
 Aşağıdaki listeden bir örnek deposuna bir iş akışı ile ilişkili olduğunda bağlı bir iş akışı kalıcı koşulları örnekleri içerir.  
  
-   Zaman bir **TransactionScope** etkinlik tamamlandıktan veya **TransactedReceiveScope** etkinliği tamamlar.  
  
-   Bir iş akışı örneği olduğunda boşta ve **WorkflowIdleBehavior** iş akışı ana bilgisayarında ayarlayın. Bu, örneğin, Mesajlaşma etkinlikleri kullanın veya bir oluşur **gecikme** etkinlik.  
  
-   Bir WorkflowApplication olduğunda boşta ve **PersistableIdle** uygulamanın özelliği ayarlanmış **PersistableIdleAction.Persist**.  
  
-   Ne zaman bir ana bilgisayar uygulaması devam veya bir iş akışı örneği unload talimatı verilir.  
  
-   Ne zaman bir iş akışı örneği sonlandırıldı veya tamamlanır.  
  
-   Zaman bir **devam ettir** etkinlik yürütür.  
  
-   Windows Workflow Foundation'ın önceki bir sürümü kullanılarak geliştirilen bir iş akışı örneği Kalıcılık noktası birlikte çalışabilir yürütme sırasında karşılaştığında.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [SQL İş Akışı Örnek Deposu](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [Örnek Depoları](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [Kalıcılık Katılımcıları](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [Kalıcılık En İyi Uygulamaları](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [Kalıcı Olmayan İş Akışı Örnekleri](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [İş Akışını Duraklatma ve Sürdürme](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
