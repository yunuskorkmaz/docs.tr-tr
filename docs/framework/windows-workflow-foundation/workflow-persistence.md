---
title: İş Akışı Kalıcılığı
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: c49e287c6132103d4bb85a8ae892a76f9b582274
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837538"
---
# <a name="workflow-persistence"></a>İş Akışı Kalıcılığı
İş akışı kalıcılığı, işlem veya bilgisayar bilgilerini bağımsız bir iş akışı örneğinin durumunun dayanıklı yakalamasıdır. Bu işlem, sistem hatası durumunda iş akışı örneği için iyi bilinen bir kurtarma noktası sağlamak ya da etkin bir şekilde iş yapmakta olmayan iş akışı örneklerini kaldırarak belleği korumak veya iş akışı örneğinin durumunu bir düğümden diğerine taşımak için yapılır bir sunucu grubundaki düğüm.  
  
 Kalıcılık, işlem çevikliği, ölçeklenebilirlik, hata durumunda kurtarma ve belleği daha verimli bir şekilde yönetme olanağı sağlar. Kalıcılık süreci, kalıcılık noktası tanımlamayı, kaydedilecek verilerin toplanması ve son olarak verilerin gerçek depolamanın bir kalıcılık sağlayıcısına devredilmesi içerir.  
  
 Bir iş akışı için kalıcılığı etkinleştirmek üzere, [nasıl yapılır: Iş akışları ve Iş akışı hizmetleri Için kalıcılığı etkinleştirme](how-to-enable-persistence-for-workflows-and-workflow-services.md)bölümünde bahsedilen bir örnek depoyu **WorkflowApplication** veya **WorkflowServiceHost** ile ilişkilendirmeniz gerekir. **WorkflowApplication** ve **WorkflowServiceHost** , kalıcı iş akışı örneklerinin bir kalıcılık deposuna etkinleştirilmesi ve iş akışı örneklerinin kalıcılık deposunda depolanan iş akışı örneği verilerine göre belleğe yüklenmesi için kendileriyle ilişkili örnek deposunu kullanır.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)], iş akışı örnekleri hakkında SQL Server 2005 veya SQL Server 2008 veritabanına verilerin ve meta verilerin kalıcılığını sağlayan **SqlWorkflowInstanceStore** sınıfıyla birlikte gelir. Daha fazla bilgi için bkz. [SQL Workflow örnek deposu](sql-workflow-instance-store.md) .  
  
 İş akışı örneğiyle ilgili bilgilerle birlikte, uygulamaya özgü verilerinizi depolamak ve yüklemek için <xref:System.Activities.Persistence.PersistenceParticipant> sınıfını genişleten Kalıcılık katılımcıları oluşturabilirsiniz. Kalıcılık Katılımcısı, özel seri hale getirilebilir verileri kalıcılık deposuna kaydetmek, örnek deposundan verileri belleğe yüklemek ve bir kalıcılık işlemi altında ek mantık gerçekleştirmek için kalıcılık sürecine katılıyorsa. Daha fazla bilgi için bkz. [Kalıcılık katılımcıları](persistence-participants.md).  
  
 Windows Server App Fabric, kalıcılığı yapılandırma sürecini basitleştirir. Daha fazla bilgi için bkz. [Windows Server App Fabric Ile Kalıcılık kavramları](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))  
  
## <a name="implicit-persistence-points"></a>Örtük Kalıcılık noktaları  
 Aşağıdaki liste, bir örnek depo bir iş akışıyla ilişkilendirildiğinde bir iş akışının kalıcı hale geçtiği koşulların örneklerini içerir.  
  
- Bir **TransactionScope** etkinliği tamamlandığında veya bir **TransactedReceiveScope** etkinliği tamamlandığında.  
  
- Bir iş akışı örneği boşta kaldığında ve **WorkflowIdleBehavior** iş akışı konağında ayarlandığında. Bu durum örneğin, mesajlaşma etkinlikleri veya bir **gecikme** etkinliği kullandığınızda oluşur.  
  
- Bir WorkflowApplication boş kaldığında ve uygulamanın **PersistableIdle** özelliği **Persistableıdıdle Action. Persist**olarak ayarlandığında.  
  
- Bir konak uygulamasına bir iş akışı örneğini kalıcı hale getirmek veya kaldırmak için talimat verilir.  
  
- Bir iş akışı örneği sonlandırıldığında veya tamamlandığında.  
  
- **Kalıcı** bir etkinlik yürütüldüğünde.  
  
- Windows Workflow Foundation önceki bir sürümü kullanılarak geliştirilen bir iş akışı örneği, birlikte çalışabilen yürütme sırasında bir kalıcılık noktasıyla karşılaştığında.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [SQL İş Akışı Örnek Deposu](sql-workflow-instance-store.md)  
  
- [Örnek Depoları](instance-stores.md)  
  
- [Kalıcılık Katılımcıları](persistence-participants.md)  
  
- [Kalıcılık En İyi Uygulamaları](persistence-best-practices.md)  
  
- [Kalıcı Olmayan İş Akışı Örnekleri](non-persisted-workflow-instances.md)  
  
- [İş Akışını Duraklatma ve Sürdürme](pausing-and-resuming-a-workflow.md)
