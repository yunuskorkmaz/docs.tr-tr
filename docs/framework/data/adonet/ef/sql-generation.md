---
title: SQL Üretimi
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 108a68f74849c7fa1418775c2a37db06d9d947ff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180588"
---
# <a name="sql-generation"></a>SQL Üretimi
Sağlayıcı için yazdığınız zaman [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], çevirme gerekir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belirli bir veritabanı için SQL Server Transact-SQL veya PL/SQL Oracle gibi anlayabilmeniz SQL içine ağaçları komutu. Bu bölümde, için SQL oluşturma bileşeni (için SELECT sorgusu) geliştirme hakkında bilgi edineceksiniz bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcısı. Ekleme hakkında bilgi için güncelleştirme ve sorguları silmek için bkz [değişiklik SQL oluşturma](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Bu bölümde anlamak için aşina olmalısınız [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve ADO.NET sağlayıcısı modeli. Komut ağaçlarının de anlamanız gerekir ve <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>SQL üretimi modülü rolü  
 SQL üretimi modülün bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcısı bir SQL:1999 hedefleyen bir tek SQL SELECT INTO deyimi belirli sorgu komut ağacı çevirir-uyumlu veritabanı. Oluşturulan SQL kadar az sorguları mümkün olduğunca iç içe. SQL üretimi modülü çıkış sorgu komut ağacı basitleştirin değil. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Örneğin ardışık filtre düğümlerinin daraltma ve birleşimler ortadan kaldırarak bunu.  
  
 <xref:System.Data.Common.DbProviderServices> Sınıftır içine komut ağaçlarını dönüştürmek için SQL oluşturma katmanında erişmek için başlangıç noktası <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Komut Ağaçlarının Şekli](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Örnek Sağlayıcısında SQL Oluşturma](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework Veri Sağlayıcısı Yazma](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
