---
title: SQL iş akışı örneği Store
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 680a233ca721cd8a0c620b797832419f460b13b6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874738"
---
# <a name="sql-workflow-instance-store"></a>SQL iş akışı örneği Store
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Bir SQL Server 2005 veya SQL Server 2008 veritabanına iş akışı durumlarda hakkındaki durum bilgilerini kalıcı hale getirmek iş akışlarını tanır SQL iş akışı örneği Store ile birlikte gelir. Bu özellik öncelikle biçiminde uygulanan <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Özet türetilen sınıfı <xref:System.Runtime.DurableInstancing.InstanceStore> Kalıcılık framework'ün sınıfı. SQL iş akışı örneği Store özelliği bir somut sürekliliğin uygulanmasını Kalıcılık komutları depoya göndermek için bir ana bilgisayar kullanan bir SQL Kalıcılık sağlayıcısı oluşturur.  
  
 SQL iş akışı örneği Store hem şirket içinde barındırılan iş akışları veya kullanan iş akışı hizmetleri destekleyen <xref:System.Activities.WorkflowApplication> veya <xref:System.ServiceModel.WorkflowServiceHost> barındırılan hizmetleri yanı sıra kullanarak <xref:System.ServiceModel.WorkflowServiceHost>. Özelliği tarafından sunulan nesne modelini kullanarak, şirket içinde barındırılan hizmetleri için SQL iş akışı örneği Store özelliği programlı bir şekilde yapılandırabilirsiniz. Bu özellik tarafından barındırılan hizmetler için yapılandırabileceğiniz <xref:System.ServiceModel.WorkflowServiceHost> nesne modelini kullanarak program aracılığıyla hem de bir XML yapılandırma dosyasını kullanarak.  
  
 SQL iş akışı örneği Store özelliği (**SqlWorkflowInstanceStore** sınıfı) uygulamıyor <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> ve bu nedenle kalıcı olmayan iş akışı WCF hizmetleri için kalıcılığı desteği sunmamaktadır. Bu ayrıca uygulamıyor <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> ve bu nedenle 3.x iş akışları için Kalıcılık desteği sunmamaktadır. Özelliği, yalnızca WF 4.0 (ve üzeri) Kalıcılık iş akışları ve iş akışı hizmetleri destekler. Bu özellik SQL Server 2005 ve SQL Server 2008 dışındaki herhangi bir veritabanına da desteklemez.  
  
 Bu bölümdeki konular, özellikleri ve SQL iş akışı örneği Store özelliklerini açıklar ve mağazası yapılandırma ayrıntıları sağlar.  
  
 Windows Server App Fabric kendi örnek deposuna ve yapılandırma ve örnek depolama kullanımını kolaylaştırmak için araçlar sağlar. Daha fazla bilgi için bkz: [Windows Server App Fabric örneği Store](https://go.microsoft.com/fwlink/?LinkId=201201). App Fabric SQL Server Kalıcılık veritabanı bakın hakkında daha fazla bilgi için [App Fabric SQL Server Kalıcılık veritabanı](https://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [SQL İş Akışı Örnek Deposunun Özellikleri](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için SQL Kalıcılığını Etkinleştirme](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [Örnek Etkinleştirme](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [Sorgu Desteği](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [Depo Genişletilebilirliği](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [Güvenlik](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [SQL Server Kalıcılık Veritabanı](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkID=177735)
