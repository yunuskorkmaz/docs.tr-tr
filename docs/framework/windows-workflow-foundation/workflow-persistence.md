---
title: İş akışı kalıcılığı
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: db0e4acc76f758004948857fc0b23a9cbc62f244
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715548"
---
# <a name="workflow-persistence"></a>İş akışı kalıcılığı
İş akışı kalıcılığı dayanıklı yakalama bir iş akışı örneği durumu, işlem veya bilgisayar bilgilerinin bağımsız olur. Bu sistem hatası durumunda iş akışı örneği için bilinen bir kurtarma noktası sağlamak veya etkin bir şekilde iş yapmamanın kaldırma iş akışı örnekleri tarafından bellek korumak için veya iş akışı örneği durumu bir düğümden diğerine taşımak için gerçekleştirilir bir sunucu grubundaki düğümü.  
  
 Kalıcılık işlemin çeviklik, ölçeklenebilirlik, Kurtarma hata ile karşılaşıldığında ve belleği daha verimli bir şekilde yönetme olanağı sağlar. Kalıcılık işlem Kalıcılık noktası, veri toplamayı ve son olarak verilerin kalıcı bir sağlayıcı gerçek depolama alanlarının kimliğini içerir.  
  
 Bir iş akışı kalıcılığını etkinleştirmek için bir örnek deposuna ile ilişkilendirmeniz gerekir **WorkflowApplication** veya **WorkflowServiceHost** belirtildiği gibi [nasıl yapılır: İş akışları ve iş akışı hizmetleri için kalıcılığı etkinleştir](how-to-enable-persistence-for-workflows-and-workflow-services.md). **WorkflowApplication** ve **WorkflowServiceHost** ilişkili örnek deposuna sürdürme deposundan ve iş akışı örneği yükleniyor kalıcı hale getirme iş akışı örnekleri etkinleştirmek için kullanın İş akışı örneği verileri sürdürme deposunda saklanan bağlı bellek.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Birlikte **SqlWorkflowInstanceStore** Kalıcılık verileri ve SQL Server 2005 veya SQL Server 2008 veritabanına iş akışı örnekleri hakkında meta veriler sağlayan sınıf. Bkz: [SQL iş akışı örneği Store](sql-workflow-instance-store.md) daha fazla ayrıntı için.  
  
 Depolayın ve iş akışı örneği ile ilgili bilgilerin yanı sıra, uygulamaya özgü verileri yüklemek için genişletme Kalıcılık katılımcıları oluşturabilirsiniz <xref:System.Activities.Persistence.PersistenceParticipant> sınıfı. Kalıcı depoya belleğe örneği Mağazası'ndan veri yüklemeye ve herhangi ek bir mantık Kalıcılık işlem altında gerçekleştirmek için özel seri hale getirilebilir veri kaydetmek için Kalıcılık işleminde bir Kalıcılık Katılımcısı katılır. Daha fazla bilgi için [Kalıcılık katılımcıları](persistence-participants.md).  
  
 Windows Server App Fabric kalıcılığını yapılandırma işlemini basitleştirir. Daha fazla bilgi için [Windows Server App Fabric ile Kalıcılık kavramları](https://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Örtük Kalıcılık noktaları  
 Aşağıdaki liste, bir örnek deposuna bir iş akışı ile ilişkili olduğunda, bir akışı kalıcı koşullar örnekleri içerir.  
  
-   Olduğunda bir **TransactionScope** etkinliği tamamlandıktan veya **TransactedReceiveScope** etkinliği tamamlar.  
  
-   Bir iş akışı örneği olduğunda boşta ve **WorkflowIdleBehavior** iş akışı konakta ayarlanır. Bu, örneğin, Mesajlaşma etkinlikleri kullandığınızda veya oluşur **gecikme** etkinlik.  
  
-   Bir WorkflowApplication olduğunda boşta ve **PersistableIdle** uygulamanın özelliği **PersistableIdleAction.Persist**.  
  
-   Ne zaman bir ana bilgisayar uygulaması kalıcı veya bir iş akışı örneği kaldırmak için talimat verilmiştir.  
  
-   Ne zaman bir iş akışı örneği sonlandırıldı veya tamamlanır.  
  
-   Olduğunda bir **kalan** etkinliği yürütür.  
  
-   Ne zaman Windows Workflow Foundation'ın önceki bir sürümü kullanılarak geliştirilen bir iş akışı örneği birlikte çalışabilen yürütme sırasında bir Kalıcılık noktası karşılaşır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [SQL İş Akışı Örnek Deposu](sql-workflow-instance-store.md)  
  
-   [Örnek Depoları](instance-stores.md)  
  
-   [Kalıcılık Katılımcıları](persistence-participants.md)  
  
-   [Kalıcılık En İyi Uygulamaları](persistence-best-practices.md)  
  
-   [Kalıcı Olmayan İş Akışı Örnekleri](non-persisted-workflow-instances.md)  
  
-   [İş Akışını Duraklatma ve Sürdürme](pausing-and-resuming-a-workflow.md)
