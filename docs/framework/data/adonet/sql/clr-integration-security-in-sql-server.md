---
title: SQL Server'da CLR tümleştirme güvenliği
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: dfd99155e42f426eeb01c89c433955cc2e3f0178
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454362"
---
# <a name="clr-integration-security-in-sql-server"></a>SQL Server'da CLR tümleştirme güvenliği
Microsoft SQL Server ortak dil çalışma zamanı (CLR) bileşen .NET Framework'ün tümleştirme sağlar. CLR tümleştirme saklı yordamlar, Tetikleyiciler, kullanıcı tanımlı türler, kullanıcı tarafından tanımlanan İşlevler, kullanıcı tanımlı toplamları ve Microsoft Visual Basic .NET veya Microsoft gibi herhangi bir .NET Framework dili kullanarak akış tablo değerli işlevler yazmanıza olanak sağlar. Visual C#.  
  
 CLR, yönetilen kod için kod erişimi güvenliği (CAS) adlı bir güvenlik modelini destekler. Bu modelde, kod meta verileri tarafından sağlanan kanıt göre derlemelere izinleri verilir. SQL Server, SQL Server'ın kullanıcı tabanlı güvenlik modeli CLR kod erişim güvenliğini modelle tümleştirir.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 SQL Server ile CLR tümleştirmesi hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Kod erişimi güvenliği](../../../../../docs/framework/misc/code-access-security.md)|.NET Framework'teki CAS açıklayan konuları içerir.|  
|[CLR tümleştirme güvenliği](/sql/relational-databases/clr-integration/security/clr-integration-security)|Yönetilen kod içinde SQL Server çalıştırmak için güvenlik modeli açıklanır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [ADO.NET’e Genel Bakış](../../../../../docs/framework/data/adonet/ado-net-overview.md)
