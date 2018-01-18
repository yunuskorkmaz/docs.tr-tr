---
title: "SQL oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6b2d4ba925af61f89b47c494f5fb17f5f9f0d995
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-generation"></a>SQL oluşturma
Sağlayıcı için yazdığınız zaman [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], çevir gerekir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] belirli bir veritabanı için SQL Server Transact-SQL veya PL/SQL Oracle için gibi anlayabileceği SQL içine ağaçları komutu. Bu bölümde, için bir SQL oluşturma bileşeni (için SELECT sorgular) geliştirme hakkında bilgi edineceksiniz bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcısı. Ekleme hakkında bilgi, güncelleştirme ve sorguları silmek için bkz: [değişikliği SQL üretimi](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Bu bölümde anlamak için aşina olmalısınız [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ve ADO.NET sağlayıcısı modeli. Komut ağaçlarını anlamanız gerekir ve <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>SQL oluşturma modülü rolü  
 SQL nesil modül, bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcı çevirir verilen sorgu komut ağacındaki bir SQL:1999 hedefleyen bir tek SQL SELECT INTO deyimi-uyumlu veritabanı. Oluşturulan SQL az sayıda sorguları mümkün olduğunca iç içe geçmiş. SQL oluşturma modülü çıkış sorgu komut ağacı basitleştirmek değil. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Bu, örneğin birleştirmeler kaldırarak ve ardışık filtre düğümlerinin daraltma işlemi yapar.  
  
 <xref:System.Data.Common.DbProviderServices> Sınıfı komutu ağaçlara dönüştürmek için SQL nesil katman erişmek için başlangıç noktasıdır <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Komut Ağaçlarının Şekli](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Komut Ağaçlarından SQL Oluşturma - En İyi Yöntemler](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Örnek Sağlayıcısında SQL Oluşturma](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework Veri Sağlayıcısı Yazma](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
