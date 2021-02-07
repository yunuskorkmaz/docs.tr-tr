---
description: 'Hakkında daha fazla bilgi edinin SQL Server: CLR tümleştirme güvenliği'
title: SQL Server’da CLR Tümleştirme Güvenliği
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 5de552c0f5b869712d2038b53abd50b8ded04747
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718544"
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
