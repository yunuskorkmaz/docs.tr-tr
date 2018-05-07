---
title: SQL Server CLR tümleştirmesi güvenliği
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 8df8a19850e9cce28b1f09e80908dafb8bfedaf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="clr-integration-security-in-sql-server"></a>SQL Server CLR tümleştirmesi güvenliği
Microsoft SQL Server, .NET Framework ortak dil çalışma zamanı (CLR) bileşeni tümleştirme sağlar. CLR tümleştirmesi, saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı türler, kullanıcı tanımlı işlevler, kullanıcı tanımlı toplamlarda ve Microsoft Visual Basic .NET ya da Microsoft gibi herhangi bir .NET Framework dil kullanarak akış tablo değerli işlevler yazma sağlar Visual C#.  
  
 CLR yönetilen kod için kod erişim güvenliği (CAS) adlı bir güvenlik modeli destekler. Bu modelde, meta verileri kod tarafından sağlanan bulgu göre derlemeler için izin verilir. SQL Server, SQL Server'ın kullanıcı tabanlı güvenlik modeli CLR kodu erişim tabanlı güvenlik modeli ile tümleşir.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 SQL Server ile CLR tümleştirme hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Kod erişimi güvenliği](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)|.NET Framework CA'LARDA açıklayan konuları içerir.|  
|[CLR tümleştirme güvenlik](http://go.microsoft.com/fwlink/?LinkId=59998)|Yönetilen kod içinde SQL Server yürütme güvenlik modeli açıklanır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
