---
title: "SQL iş akışı örneği deposu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bf78f3b966b006d002771414551412ea0208e30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="sql-workflow-instance-store"></a>SQL iş akışı örneği deposu
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] İş akışı örneği bir SQL Server 2005 veya SQL Server 2008 veritabanı ile ilgili durum bilgisini kalıcı hale getirmek için iş akışlarını tanır SQL iş akışı örneği deposu ile birlikte gelir. Bu özellik öncelikle biçiminde uygulanan <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Özet türeyen sınıf <xref:System.Runtime.DurableInstancing.InstanceStore> Kalıcılık framework'ün sınıfı. SQL iş akışı örneği depolama özelliğini Kalıcılık komutları mağazaya göndermek için bir konak kullanır API Kalıcılık somut bir uygulamasıdır SQL Kalıcılık sağlayıcısı meydana gelir.  
  
 SQL iş akışı örneği deposuna kendini barındıran iş akışları veya kullanan iş akışı hizmetleri destekleyen <xref:System.Activities.WorkflowApplication> veya <xref:System.ServiceModel.WorkflowServiceHost> barındırılan hizmetleri yanı sıra kullanarak <xref:System.ServiceModel.WorkflowServiceHost>. Özelliği tarafından sunulan nesne modelini kullanarak kendini barındıran Hizmetleri için SQL iş akışı örneği depolama özelliği programlı olarak yapılandırabilirsiniz. Bu özellik tarafından barındırılan hizmetler için yapılandırabileceğiniz <xref:System.ServiceModel.WorkflowServiceHost> nesne modelini kullanarak programlı olarak hem de bir XML yapılandırma dosyası kullanarak.  
  
 SQL iş akışı örneği depolama özelliğini (**SqlWorkflowInstanceStore** sınıfı) uygulamayan <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> ve bu nedenle dayanıklı iş akışı olmayan WCF hizmetleri için Kalıcılık destek sağlamaz. Bu ayrıca uygulamayan <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> ve bu nedenle 3.x iş akışları için Kalıcılık destek sağlamaz. Özelliği, yalnızca WF 4.0 için (ve daha sonra) Kalıcılık iş akışları ve iş akışı hizmetleri destekler. Özellik SQL Server 2005 ve SQL Server 2008 dışındaki tüm veritabanlarını da desteklemez.  
  
 Bu bölümdeki konularda SQL iş akışı örneği deposunun özellikleri açıklamak ve depolama yapılandırma hakkında ayrıntılar sağlar.  
  
 Windows Server App Fabric kendi örnek deposuna ve yapılandırmayı ve örnek deposuna kullanımını kolaylaştırmak için araç sağlar. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]bkz: [Windows Server App Fabric örnek deposuna](http://go.microsoft.com/fwlink/?LinkId=201201). [!INCLUDE[crabout](../../../includes/crabout-md.md)]Uygulama doku SQL Server Kalıcılık veritabanı bakın [uygulama doku SQL Server Kalıcılık veritabanı](http://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
-   [SQL iş akışı örneği deposu özellikleri](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [Nasıl yapılır: iş akışları ve iş akışı hizmetleri için SQL kalıcılığı etkinleştir](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [Örnek etkinleştirme](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [Sorgular için destek](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [Depolama genişletilebilirliği](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [Güvenlik](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [SQL Server Kalıcılık veritabanı](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kalıcılık örnekleri](http://go.microsoft.com/fwlink/?LinkID=177735)
