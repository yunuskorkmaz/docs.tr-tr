---
title: SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d9fe0f03c88584607c6bc38fcbcff3f9424fd40c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183032"
---
# <a name="sql-server-common-language-runtime-integration"></a>SQL Server Ortak Dil Çalışma Zamanı Modülü Tümleştirmesi

SQL Server 2005, Microsoft Windows için .NET Framework ortak dil çalışma zamanı (CLR) bileşeninin tümleştirilmesine tanıtılmıştır. Bu, Microsoft Visual Basic .NET ve Microsoft Visual C# dahil olmak üzere herhangi bir .NET Framework dilini kullanarak saklı yordamları, Tetikleyicileri, Kullanıcı tanımlı türleri, Kullanıcı tanımlı özellikleri, Kullanıcı tanımlı toplamları ve akış tablosu değerli işlevleri yazabileceğiniz anlamına gelir. <xref:Microsoft.SqlServer.Server>Ad alanı, yönetilen kodun Microsoft SQL Server ortamıyla etkileşime girebilmesi için bir dizi yeni uygulama programlama arabirimi (API) içerir.  
  
 Bu bölümde, SQL Server ortak dil çalışma zamanı (CLR) tümleştirmesine özgü özellikler ve davranışlar ve ADO.NET için işleme özgü SQL Server uzantıları açıklanmaktadır.  
  
 Bu bölüm, SQL Server CLR tümleştirmesiyle çalışmaya başlamak için yalnızca yeterli bilgi sağlamak amacıyla tasarlanmıştır ve kapsamlı bir şekilde değildir. Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **SQL Server belgeleri**  
  
1. [Ortak dil çalışma zamanı (CLR) tümleştirme programlama kavramları](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [SQL Server CLR Tümleştirmesine Giriş](introduction-to-sql-server-clr-integration.md)  
 CLR tümleştirmesi SQL Server için bir giriş sağlar. Ek konuların bağlantılarını sağlar.  
  
 [Kullanıcı Tanımlı CLR İşlevleri](clr-user-defined-functions.md)  
 Çeşitli CLR işlevleri türlerinin nasıl uygulanacağını ve kullanılacağını açıklar: tablo değerli, skaler ve Kullanıcı tanımlı toplama işlevleri.  
  
 [Kullanıcı Tanımlı CLR Türleri](clr-user-defined-types.md)  
 CLR kullanıcı tanımlı türlerin nasıl uygulanacağını ve kullanılacağını açıklar. Ek konuların bağlantılarını sağlar.  
  
 [CLR Saklı Yordamları](clr-stored-procedures.md)  
 CLR saklı yordamlarının nasıl uygulanacağını ve kullanılacağını açıklar. Ek konuların bağlantılarını sağlar.  
  
 [CLR Tetikleyicileri](clr-triggers.md)  
 CLR tetikleyicilerinin nasıl uygulanacağını ve kullanılacağını açıklar. Ek konuların bağlantılarını sağlar.  
  
 [Bağlam Bağlantısı](the-context-connection.md)  
 Bağlam bağlantısını açıklar.  
  
 [SQL Server İşlem İçine Özgü ADO.NET Davranışı](sql-server-in-process-specific-behavior-of-adonet.md)  
 ADO.NET öğesine ve bağlam bağlantısına yönelik işleme özgü uzantıları SQL Server açıklar. Ek konuların bağlantılarını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
