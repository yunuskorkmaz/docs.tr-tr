---
title: SQL İş Akışı Örnek Deposu
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 1764017369e82cfbed38be06b4a36847576b5fc0
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837642"
---
# <a name="sql-workflow-instance-store"></a>SQL İş Akışı Örnek Deposu
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], iş akışlarının bir SQL Server 2005 veya SQL Server 2008 veritabanındaki iş akışı örnekleri hakkındaki durum bilgilerini kalıcı hale getirebileceği SQL Iş akışı örneği deposuyla birlikte gelir. Bu özellik birincil olarak, kalıcılık çerçevesinin soyut <xref:System.Runtime.DurableInstancing.InstanceStore> sınıfından türetilen <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> sınıfı biçiminde uygulanır. SQL Iş akışı örneği deposu özelliği, bir konağın kalıcı komutları depoya göndermek için kullandığı Kalıcılık API 'si için somut bir uygulama olan bir SQL kalıcılık sağlayıcısı oluşturur.  
  
 SQL Iş akışı örneği deposu hem şirket içinde barındırılan iş akışlarını hem de <xref:System.Activities.WorkflowApplication> veya <xref:System.ServiceModel.WorkflowServiceHost> kullanan iş akışı hizmetlerini ve ' de barındırılan Hizmetleri destekler <xref:System.ServiceModel.WorkflowServiceHost>kullanıyor. Şirket içinde barındırılan hizmetler için SQL Iş akışı örnek deposu özelliğini, özelliği tarafından sunulan nesne modelini kullanarak programlı bir şekilde yapılandırabilirsiniz. Bu özelliği, nesne modelini kullanarak ve ayrıca bir XML yapılandırma dosyası kullanarak <xref:System.ServiceModel.WorkflowServiceHost> tarafından barındırılan hizmetler için yapılandırabilirsiniz.  
  
 SQL Iş akışı örnek deposu özelliği (**SqlWorkflowInstanceStore** sınıfı) <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> uygulamaz ve bu nedenle dayanıklı iş akışı olmayan WCF Hizmetleri için kalıcılık desteği sunmaz. Ayrıca, <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> uygulamaz ve bu nedenle 3. x iş akışları için kalıcılık desteği sunmaz. Özelliği yalnızca WF 4,0 (ve üzeri) iş akışları ve iş akışı hizmetleri için kalıcılığı destekler. Özelliği ayrıca SQL Server 2005 ve SQL Server 2008 dışındaki veritabanlarını desteklemez.  
  
 Bu bölümdeki konular, SQL Iş akışı örnek deposunun özelliklerini ve özelliklerini anlatmaktadır ve mağazayı yapılandırma hakkında ayrıntılı bilgi sağlar.  
  
 Windows Server App Fabric, örnek deposunun yapılandırmasını ve kullanımını basitleştirmek için kendi örnek deposunu ve araçları sağlar. Daha fazla bilgi için bkz. [Windows Server App Fabric örnek deposu](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)). App Fabric SQL Server kalıcılık veritabanı hakkında daha fazla bilgi için bkz. [App fabric SQL Server kalıcılık veritabanı](https://docs.microsoft.com/previous-versions/appfabric/ee790819(v=azure.10))  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [SQL İş Akışı Örnek Deposunun Özellikleri](properties-of-sql-workflow-instance-store.md)  
  
- [Nasıl yapılır: İş Akışları ve İş Akışı Hizmetleri için SQL Kalıcılığını Etkinleştirme](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [Örnek Etkinleştirme](instance-activation.md)  
  
- [Sorgu Desteği](support-for-queries.md)  
  
- [Depo Genişletilebilirliği](store-extensibility.md)  
  
- [Security](security.md)  
  
- [SQL Server Kalıcılık Veritabanı](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kalıcılık örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))
