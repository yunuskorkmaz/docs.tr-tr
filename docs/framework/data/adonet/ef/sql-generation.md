---
title: SQL Üretimi
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854359"
---
# <a name="sql-generation"></a>SQL Üretimi
Entity Framework için bir sağlayıcı yazdığınızda, Entity Framework komut ağaçlarını belirli bir veritabanının anlayabilmesi için, SQL Server için Transact-SQL veya Oracle için PL/SQL gibi bir SQL 'e çevirmeniz gerekir. Bu bölümde, bir Entity Framework sağlayıcısı için SQL oluşturma bileşeni (seçme sorguları için) geliştirmeyi öğreneceksiniz. Ekleme, güncelleştirme ve silme sorguları hakkında daha fazla bilgi için bkz. [DEĞIŞIKLIK SQL oluşturma](modification-sql-generation.md).  
  
 Bu bölümü anlamak için Entity Framework ve ADO.NET sağlayıcı modeliyle ilgili bilgi sahibi olmanız gerekir. Komut ağaçlarını ve <xref:System.Data.Common.CommandTrees.DbExpression>de anlamanız gerekir.  
  
## <a name="the-role-of-the-sql-generation-module"></a>SQL oluşturma modülünün rolü  
 Bir Entity Framework sağlayıcının SQL oluşturma modülü, belirli bir sorgu komut ağacını SQL: 1999 ile uyumlu bir veritabanını hedefleyen tek bir SQL SELECT ifadesine dönüştürür. Oluşturulan SQL 'in mümkün olduğunca az sayıda iç içe sorgusu olmalıdır. SQL oluşturma modülü çıkış sorgusu komut ağacını basitleştirmemelidir. Entity Framework, bu, örneğin birleştirmeleri ortadan kaldırarak ve ardışık filtre düğümlerini daraltarak bu şekilde yapılır.  
  
 Sınıfı, komut <xref:System.Data.Common.DbCommand>ağaçlarını dönüştürmek için SQL oluşturma katmanına erişmenin başlangıç noktasıdır. <xref:System.Data.Common.DbProviderServices>  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Komut Ağaçlarının Şekli](the-shape-of-the-command-trees.md)  
  
 [Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler](generating-sql-from-command-trees-best-practices.md)  
  
 [Örnek Sağlayıcısında SQL Oluşturma](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework Veri Sağlayıcısı Yazma](writing-an-ef-data-provider.md)
