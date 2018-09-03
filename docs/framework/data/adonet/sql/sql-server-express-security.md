---
title: SQL Server Express Security
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: 736c450d944efe7e6a69e16e00e1c96f0a868697
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485592"
---
# <a name="sql-server-express-security"></a>SQL Server Express Security
Microsoft SQL Server Express Edition (SQL Server Express), Microsoft SQL Sunucusu'nu temel alır ve Veritabanı Altyapısı'nın özelliklerinin birçoğunu destekler. Önemsiz özellik ve ağ bağlantısı varsayılan olarak kapalı olan şekilde tasarlanmıştır. Bu saldırı kötü niyetli bir kullanıcı tarafından kullanılabilir yüzey alanını azaltır.  
  
 SQL Server Express, genellikle adlandırılmış bir örneği yüklenir. Örneğin varsayılan addır `SQLExpress`. Adlandırılmış bir örnek, bilgisayarın ağ adı yanı sıra, yükleme sırasında belirttiğiniz örnek adı tarafından tanımlanır.  
  
## <a name="network-access"></a>Ağ erişimi  
 Güvenlik nedenleriyle, varsayılan olarak SQL Server Express ağ protokolleri devre dışı bırakılır. Bu SQL Server Express örneğini barındıran bilgisayarın tehlikeye atabilir dış kullanıcılardan gelen saldırıları engeller. Açıkça ağ bağlantısı etkinleştirmeli ve başka bir bilgisayardan bir SQL Server Express örneğine bağlanmak için SQL Server Browser hizmetini başlatın.  
  
 Ağ bağlantısı etkinleştirildikten sonra bir SQL Server Express örneği SQL Server'ın başka sürümleri aynı güvenlik gereksinimlerine sahiptir.  
  
## <a name="user-instances"></a>Kullanıcı örnekleri  
 Bir kullanıcı örneği oluşturulan SQL Server Express veritabanı motoru tarafından bir üst SQL Server Express örneğini ayrı bir örneğidir. Windows sistem yöneticisinin en az ayrıcalıklı kullanıcı hesabı altında çalışan kullanıcılar izin vermek için birincil amacı, bir kullanıcı örneği olduğunu (`sysadmin`), yerel bilgisayardaki SQL Server Express örneği üzerinde ayrıcalıkları. Kullanıcı örnekleri kendi bilgisayarlarındaki sistem yöneticisi olan kullanıcılar için tasarlanmamıştır.  
  
 Birincil bir SQL Server veya SQL Server Express örneğini bir kullanıcı adına bir kullanıcı örneği oluşturulur. Bu işlem bir kullanıcı işlemi kullanıcının, bir hizmet olarak Windows güvenlik bağlamı altında çalışır. SQL Server oturumları izin verilmiyor; yalnızca Windows oturumları desteklenir. Bu kullanıcı, gerçekleştirmek için izne sahip olmayan sistem genelinde değişiklikler yapmasını bir kullanıcı örneği üzerinde yazılım yürütülürken engeller. Bir kullanıcı örneği olarak da bilinen bir alt veya istemci örneği olan ve bazen nedeniyle RANU kısaltması ("normal kullanıcı olarak çalıştır") kullanılarak adlandırılır.  
  
 Her bir kullanıcı örneği, kendi üst örneğini ve aynı bilgisayarda çalışan diğer kullanıcı örneklerden yalıtılır. Kullanıcı örneklerinde yüklü veritabanları yalnızca tek kullanıcı modunda açılan; birden çok kullanıcı kendisine bağlanamıyor. Çoğaltma, dağıtılmış sorgular ve uzak bağlantıları kullanıcı örnekleri için devre dışı bırakıldı. Bir kullanıcı örneğine bağlandığında, kullanıcılar üst SQL Server Express örneği üzerinde özel ayrıcalıklarına sahip.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 SQL Server Express hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|||  
|-|-|  
|[SQL Server Çevrimiçi Kitapları](https://msdn.microsoft.com/library/bb543165.aspx)|SQL Server Express için belgelerini içerir.|  
|[SQL Server Express'e bağlanma](https://msdn.microsoft.com/library/ms165679.aspx) SQL Server Çevrimiçi Kitapları'nda|Bir ağ üzerinde SQL Server Express Edition kullanmayı açıklar.|  
|[Microsoft SQL Server 2005 Express Edition çevrimiçi kitaplar](https://msdn.microsoft.com/library/ms165706.aspx)|SQL Server 2005 Express Edition için kapsamlı belgeler sağlar.|  
|[Yönetici olmayanlar için kullanıcı örnekleri](https://msdn.microsoft.com/library/ms143684.aspx) SQL Server Çevrimiçi Kitapları'nda|Kullanıcı örnekleri oluşturup dağıtmayı açıklar.|  
|[SQL Server Express Kullanıcı Örnekleri](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|Bir ADO.NET uygulamasında kullanıcı örneği yeteneklerini açıklar. Bir kullanıcı örneği etkinleştirmek için bir kullanıcı örneği kullanarak bağlanma hakkında bilgi sağlayan bir <xref:System.Data.SqlClient.SqlConnection>, kullanıcı örneği ömrünü ve kullanıcı örneği senaryoları.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [SQL Server Express Kullanıcı Örnekleri](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
