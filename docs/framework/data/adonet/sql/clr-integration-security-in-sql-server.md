---
title: SQL Server’da CLR Tümleştirme Güvenliği
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: e5d15b4e5ac36f7ecddf45179c65a60995a1a578
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147781"
---
# <a name="clr-integration-security-in-sql-server"></a>SQL Server’da CLR Tümleştirme Güvenliği

Microsoft SQL Server, .NET Framework ortak dil çalışma zamanı (CLR) bileşeninin tümleştirmesini sağlar. CLR tümleştirmesi saklı yordamlar, Tetikleyiciler, Kullanıcı tanımlı türler, Kullanıcı tanımlı işlevler, Kullanıcı tanımlı toplamalar ve akış tablo değerli işlevlerini, Microsoft Visual Basic .NET veya Microsoft Visual C# gibi .NET Framework herhangi bir dili kullanarak yazmanızı sağlar.  
  
 CLR, yönetilen kod için kod erişim güvenliği (CAS) adlı bir güvenlik modelini destekler. Bu modelde, meta verilerde kodun sağladığı kanıtları temel alan derlemelere izinler verilir. SQL Server, SQL Server Kullanıcı tabanlı güvenlik modelini CLR 'nin kod erişim tabanlı güvenlik modeliyle tümleştirir.  
  
## <a name="external-resources"></a>Dış Kaynaklar  

 SQL Server ile CLR tümleştirmesi hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Kod erişim güvenliği](../../../misc/code-access-security.md)|.NET Framework CA 'ları açıklayan konuları içerir.|  
|[CLR tümleştirme güvenliği](/sql/relational-databases/clr-integration/security/clr-integration-security)|SQL Server içinde yürütülen yönetilen kod için güvenlik modelini açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi](sql-server-common-language-runtime-integration.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
