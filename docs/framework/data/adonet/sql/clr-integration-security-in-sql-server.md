---
title: SQL Server’da CLR Tümleştirme Güvenliği
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 4756d13ff52a4c55b48c3ea56d26111029c8a7e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794563"
---
# <a name="clr-integration-security-in-sql-server"></a>SQL Server’da CLR Tümleştirme Güvenliği
Microsoft SQL Server, .NET Framework ortak dil çalışma zamanı (CLR) bileşeninin tümleştirmesini sağlar. CLR tümleştirmesi saklı yordamlar, Tetikleyiciler, Kullanıcı tanımlı türler, Kullanıcı tanımlı işlevler, Kullanıcı tanımlı toplamalar ve akış tablo değerli işlevler, Microsoft Visual Basic .NET veya Microsoft gibi herhangi bir .NET Framework dil kullanarak yazmanızı sağlar. Görsel C#.  
  
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
