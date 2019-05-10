---
title: 'Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 3feb045ff29527c388e1aa190108f003f96dd4d0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596783"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Nasıl yapılır: Visual Basic veya C içinde nesne modeli oluşturma\#
İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], programlama diliniz bir nesne modelinde bir ilişkisel veritabanına eşlendi. İki aracı bir Visual Basic otomatik olarak oluşturmak için kullanılabilir veya C# var olan bir veritabanının meta verilerden model.  
  
- Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturmak için. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Oluşturmanıza yardımcı olmak için zengin kullanıcı arabirimi sağlayan bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli. Daha fazla bilgi edinmek, [LINQ to SQL araçlarını Visual Studio'da](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- SQLMetal komut satırı aracı. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Bir mevcut veritabanını ve bir nesne modeli oluşturmak için istediğiniz yoksa, nesne modeli kod kullanarak düzenleyici oluşturabilirsiniz ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Daha fazla bilgi için [nasıl yapılır: Dinamik olarak veritabanı oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Belgeler için [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] bir Visual Basic oluşturmayı örnekler sağlar veya C# nesne modelini kullanarak [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. SQLMetal komut satırı aracı kullanma örnekleri aşağıdaki bilgileri sağlayın. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 SQLMetal komut satırında aşağıdaki örnekte gösterildiği, Northwind örnek veritabanındaki nesne öznitelik tabanlı model olarak Visual Basic kod oluşturur. Saklı yordamları ve işlevleri de işlenir.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilen SQLMetal komut satırı oluşturur C# Northwind örnek veritabanıyla kurulan öznitelik tabanlı nesne modeli kodu. Saklı yordamları ve işlevleri de oluşturulur ve tablo adları otomatik olarak pluralized.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Nasıl yapılır: Kod Düzenleyicisi'ni kullanarak varlık sınıflarını özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Öznitelik Tabanlı Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [SqlMetal.exe (Kod Üretme Aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Dış Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
