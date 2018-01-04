---
title: "SQL Server Express güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 77658b1c4b40090b8e532f1a0566ecb927328d65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-express-security"></a>SQL Server Express güvenliği
Microsoft SQL Server Express Edition (SQL Server Express) Microsoft SQL Sunucusu'nu temel alır ve Veritabanı Altyapısı'nın özelliklerin çoğunu destekler. Böylece gereksiz özellikleri ve ağ bağlantısını varsayılan olarak kapalı olan tasarlanmıştır. Bu saldırı kötü niyetli bir kullanıcı tarafından kullanılabilir yüzey alanını azaltır.  
  
 SQL Server Express genellikle adlandırılmış bir örnek yüklenir. Varsayılan adı örneği `SQLExpress`. Adlandırılmış bir örnek, bilgisayarın ağ adına ve yükleme sırasında belirttiğiniz örnek adı tarafından tanımlanır.  
  
## <a name="network-access"></a>Ağ erişimi  
 Güvenlik nedenleriyle, ağ protokolleri SQL Server Express varsayılan olarak devre dışı. Bu SQL Server Express örneğini barındıran bilgisayarda tehlikeye atabilir dış kullanıcıların saldırılarını önler. Açıkça ağ bağlantısını etkinleştirmeli ve başka bir bilgisayardan bir SQL Server Express örneğine bağlanmak için SQL Server Browser hizmetini başlatın.  
  
 Ağ bağlantısı etkinleştirildiğinde, bir SQL Server Express örneğini bir SQL Server sürümleri aynı güvenlik gereksinimlerine sahiptir.  
  
## <a name="user-instances"></a>Kullanıcı örnekleri  
 Bir kullanıcı örneği oluşturulan SQL Server Express veritabanı motoru tarafından bir üst SQL Server Express örneğini ayrı bir örneğidir. Windows Sistem Yöneticisi için en az ayrıcalıklı kullanıcı hesabı altında çalıştıran kullanıcılar izin vermek için bir kullanıcı örneği birincil amacı olan (`sysadmin`) ayrıcalıklarına kendi yerel bilgisayardaki SQL Server Express örneği. Kullanıcı örnekleri kendi bilgisayarlarındaki sistem yöneticisi olan kullanıcılar için tasarlanmamıştır.  
  
 Birincil bir SQL Server veya SQL Server Express örneğini bir kullanıcı adına bir kullanıcı örneği oluşturulur. Bu kullanıcı işlemi kullanıcı, bir hizmet olarak değil, Windows güvenlik bağlamı altında çalışır. SQL Server oturumları izin verilmiyor; yalnızca Windows oturumu açma desteklenir. Bu kullanıcı, yapmak için izinlere sahip değil sistem genelinde değişiklik yapmasını kullanıcı örneği üzerinde yazılım yürütme önler. Bir kullanıcı örneği olarak da bilinen bir alt veya istemci örneğidir ve bazen ("normal kullanıcı olarak çalıştır") nedeniyle RANU kısaltma kullanarak denir.  
  
 Her bir kullanıcı örneği, kendi üst örneği ve aynı bilgisayarda çalışan diğer kullanıcı örnekleri'ndan yalıtılır. Kullanıcı örneklerinde yüklü veritabanları yalnızca tek kullanıcı modunda açılır; birden çok kullanıcı için bağlantı kuramıyor. Çoğaltma, dağıtılmış sorgular ve uzak bağlantıları kullanıcı örnekleri için devre dışı bırakılır. Bir kullanıcı örneğine bağlandığında, kullanıcılar üst SQL Server Express örneği üzerinde hiçbir özel ayrıcalıklara sahip değilsiniz.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 SQL Server Express hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|||  
|-|-|  
|[SQL Server Çevrimiçi Kitapları](http://msdn.microsoft.com/library/bb543165.aspx)|SQL Server Express için belgelerini içerir.|  
|[SQL Server Express'e bağlanma](http://msdn.microsoft.com/library/ms165679.aspx) SQL Server Çevrimiçi Kitapları'nda|Bir ağ üzerinde SQL Server Express Edition kullanmayı açıklar.|  
|[Microsoft SQL Server 2005 Express Edition Çevrimiçi Kitapları](http://msdn.microsoft.com/library/ms165706.aspx)|SQL Server 2005 Express Edition için belgeleri tamamlayın.|  
|[Yönetici olmayanlar için kullanıcı örnekleri](http://msdn.microsoft.com/library/ms143684.aspx) SQL Server Çevrimiçi Kitapları'nda|Kullanıcı örnekleri oluşturup açıklar.|  
|[SQL Server Express Kullanıcı Örnekleri](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|Bir ADO.NET uygulamasında kullanıcı örneği özellikleri açıklanmaktadır. Bir kullanıcı örneği etkinleştirmek için bir kullanıcı örneği kullanarak bağlanma hakkında bilgi sağlayan bir <xref:System.Data.SqlClient.SqlConnection>, kullanıcı örneği yaşam süresi ve kullanıcı örnek senaryoları.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [SQL Server Express Kullanıcı Örnekleri](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
