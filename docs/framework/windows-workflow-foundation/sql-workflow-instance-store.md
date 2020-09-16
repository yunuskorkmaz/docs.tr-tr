---
title: SQL İş Akışı Örnek Deposu
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 38cf83ebb8417009c6aa205aa29cd633d1232f0a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540238"
---
# <a name="sql-workflow-instance-store"></a>SQL İş Akışı Örnek Deposu
, İş [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] akışlarının bir SQL Server 2005 veya SQL Server 2008 veritabanındaki iş akışı örnekleri hakkında durum bilgilerini kalıcı hale GETIREBILECEĞI SQL Iş akışı örnek deposu ile birlikte gelir. Bu özellik, birincil olarak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Kalıcılık çerçevesinin soyut sınıfından türetilen sınıf biçiminde uygulanır <xref:System.Runtime.DurableInstancing.InstanceStore> . SQL Iş akışı örneği deposu özelliği, bir konağın kalıcı komutları depoya göndermek için kullandığı Kalıcılık API 'si için somut bir uygulama olan bir SQL kalıcılık sağlayıcısı oluşturur.  
  
 SQL Iş akışı örneği deposu hem şirket içinde barındırılan hem de kullanan <xref:System.Activities.WorkflowApplication> <xref:System.ServiceModel.WorkflowServiceHost> hizmetlerin yanı sıra kendi kendine barındırılan iş akışlarını veya iş akışı hizmetlerini destekler <xref:System.ServiceModel.WorkflowServiceHost> . Şirket içinde barındırılan hizmetler için SQL Iş akışı örnek deposu özelliğini, özelliği tarafından sunulan nesne modelini kullanarak programlı bir şekilde yapılandırabilirsiniz. Bu özelliği <xref:System.ServiceModel.WorkflowServiceHost> , nesne modelini kullanarak ve ayrıca BIR XML yapılandırma dosyası kullanarak, aracılığıyla barındırılan hizmetler için yapılandırabilirsiniz.  
  
 SQL Iş akışı örnek deposu özelliği (**SqlWorkflowInstanceStore** sınıfı) uygulamaz <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> ve bu nedenle dayanıklı Iş akışı olmayan WCF Hizmetleri için kalıcılık desteği sunmaz. Ayrıca, uygulamaz <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> ve bu nedenle 3. x iş akışları için kalıcılık desteği sunmaz. Özelliği yalnızca WF 4,0 (ve üzeri) iş akışları ve iş akışı hizmetleri için kalıcılığı destekler. Özelliği ayrıca SQL Server 2005 ve SQL Server 2008 dışındaki veritabanlarını desteklemez.  
  
 Bu bölümdeki konular, SQL Iş akışı örnek deposunun özelliklerini ve özelliklerini anlatmaktadır ve mağazayı yapılandırma hakkında ayrıntılı bilgi sağlar.  
  
 Windows Server App Fabric, örnek deposunun yapılandırmasını ve kullanımını basitleştirmek için kendi örnek deposunu ve araçları sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric örnek deposu](/previous-versions/appfabric/ff383417(v=azure.10)). App Fabric SQL Server kalıcılık veritabanı hakkında daha fazla bilgi için bkz. [App fabric SQL Server kalıcılık veritabanı](/previous-versions/appfabric/ee790819(v=azure.10))  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [SQL İş Akışı Örnek Deposunun Özellikleri](properties-of-sql-workflow-instance-store.md)  
  
- [Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için SQL Kalıcılığını Etkinleştirme](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [Örnek Etkinleştirme](instance-activation.md)  
  
- [Sorgu Desteği](support-for-queries.md)  
  
- [Depo Genişletilebilirliği](store-extensibility.md)  
  
- [Güvenlik](security.md)  
  
- [SQL Server Kalıcılık Veritabanı](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kalıcılık örnekleri](/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))
