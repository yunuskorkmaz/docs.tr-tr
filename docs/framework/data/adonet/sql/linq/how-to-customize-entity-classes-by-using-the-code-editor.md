---
title: "Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 68a28e25cf07ec3d84cc7bb12734594ca55e7e0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a>Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme
Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] oluşturmak veya kendi sınıflar özelleştirme.  
  
 Aynı zamanda [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] Kod düzenleyicisinde kendi eşleme kod yazmaya veya zaten oluşturulmuş kodu özelleştirmek için. Daha fazla bilgi için bkz: [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
 Bu bölümdeki konular, nesne modeli özelleştirmeyi açıklar.  
  
 [Nasıl yapılır: Veritabanı Adları Belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
 [Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
 [Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
 [Nasıl yapılır: Birincil Anahtarları Temsil Etme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
 [Nasıl yapılır: Veritabanı İlişkilerini Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 Kullanım örnekleri sağlar <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği.  
  
 [Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.  
  
 [Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 [Nasıl yapılır: Veritabanı Veri Türleri Belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
 [Nasıl yapılır: Hesaplanan Sütunları Temsil Etme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
 [Nasıl yapılır: Özel Depolama Alanları Belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.  
  
 [Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
 [Nasıl yapılır: Devralma Hiyerarşilerini Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 Devralma Hiyerarşisi belirtmek için gerekli eşlemeleri açıklar.  
  
 [Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SqlMetal.exe (Kod Üretme Aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
