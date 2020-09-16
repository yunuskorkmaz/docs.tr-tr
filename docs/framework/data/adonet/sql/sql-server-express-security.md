---
title: SQL Server Express Güvenliği
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: 503b23602752375006b1a32a342af8a7789596b2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552732"
---
# <a name="sql-server-express-security"></a>SQL Server Express Güvenliği
Microsoft SQL Server Express Edition (SQL Server Express) Microsoft SQL Server tabanlıdır ve veritabanı altyapısının özelliklerinin çoğunu destekler. Bu, varsayılan olarak önemli olmayan özelliklerin ve ağ bağlantılarının kapalı olmasını sağlayacak şekilde tasarlanmıştır. Bu, kötü niyetli bir kullanıcı tarafından saldırı için kullanılabilen yüzey alanını azaltır.  
  
 SQL Server Express genellikle adlandırılmış bir örnek olarak yüklenir. Örneğin varsayılan adı `SQLExpress` . Adlandırılmış bir örnek, bilgisayarın ağ adı ve yükleme sırasında belirttiğiniz örnek adı ile tanımlanır.  
  
## <a name="network-access"></a>Ağ erişimi  
 Güvenlik nedenleriyle, ağ protokolleri SQL Server Express varsayılan olarak devre dışıdır. Bu, SQL Server Express örneğini barındıran bilgisayarın güvenliğini tehlikeye atabilecek kullanıcılardan dışarıdan saldırıları engeller. Ağ bağlantısını açıkça etkinleştirmeniz ve başka bir bilgisayardan bir SQL Server Express örneğine bağlanmak için SQL Server Browser hizmeti başlatmanız gerekir.  
  
 Ağ bağlantısı etkinleştirildikten sonra, bir SQL Server Express örneği, diğer SQL Server sürümleriyle aynı güvenlik gereksinimlerine sahiptir.  
  
## <a name="user-instances"></a>Kullanıcı örnekleri  
 Bir kullanıcı örneği, bir SQL Server Express üst örneği tarafından oluşturulan SQL Server Express veritabanı altyapısının ayrı bir örneğidir. Bir Kullanıcı örneğinin birincil hedefi, en az ayrıcalıklı kullanıcı hesabı altında Windows çalıştıran kullanıcıların, `sysadmin` Yerel bilgisayarlarındaki SQL Server Express örneğinde Sistem Yöneticisi () ayrıcalıklarına sahip olmasını sağlamaktır. Kullanıcı örnekleri, kendi bilgisayarlarında sistem yöneticileri olan kullanıcılara yönelik değildir.  
  
 Bir kullanıcı örneği, bir kullanıcı adına SQL Server veya SQL Server Express birincil örneğinden oluşturulur. Bir hizmet olarak değil kullanıcının Windows güvenlik bağlamı altında Kullanıcı işlemi olarak çalışır. SQL Server oturum açma işlemlerine izin verilmiyor; yalnızca Windows oturum açmaları desteklenir. Bu, bir Kullanıcı örneğinde yürütülen yazılımın, kullanıcının yapma iznine sahip olmadığı sistem genelinde değişiklikler yapmasına engel olur. Bir kullanıcı örneği, alt veya istemci örneği olarak da bilinir ve bazen RANU kısaltması ("normal kullanıcı olarak çalıştır") kullanılarak da adlandırılır.  
  
 Her kullanıcı örneği, üst örneğinden ve aynı bilgisayarda çalışan diğer kullanıcı örneklerinden yalıtılmıştır. Kullanıcı örneklerine yüklenen veritabanları yalnızca tek kullanıcılı modda açılır. birden çok Kullanıcı bu dosyalara bağlanamaz. Çoğaltma, dağıtılmış sorgular ve uzak bağlantılar Kullanıcı örnekleri için devre dışıdır. Bir kullanıcı örneğine bağlanıldığında, kullanıcıların üst SQL Server Express örneği üzerinde özel ayrıcalıkları yoktur.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 SQL Server Express hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition Books Online](/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|SQL Server 2005 Express Sürüm için tüm belgeler.|  
|SQL Server Books Online 'da [yönetici olmayanlar Için Kullanıcı örnekleri](/previous-versions/sql/sql-server-2008/ms143684(v=sql.100))|Kullanıcı örneklerinin nasıl oluşturulacağını ve dağıtılacağını açıklar.|  
|[SQL Server Express Kullanıcı Örnekleri](sql-server-express-user-instances.md)|Bir ADO.NET uygulamasındaki Kullanıcı örneği yeteneklerini açıklar. Kullanıcı örneğini etkinleştirme, Kullanıcı örneği ömrü ve Kullanıcı örneği senaryoları kullanarak bir kullanıcı örneğine bağlanma hakkında bilgi sağlar <xref:System.Data.SqlClient.SqlConnection> .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Güvenliği](sql-server-security.md)
- [SQL Server Express Kullanıcı Örnekleri](sql-server-express-user-instances.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
