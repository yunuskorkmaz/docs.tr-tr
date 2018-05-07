---
title: 'Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 806d0ebc0e9ce970e144d80dbbd4910f9d271e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma
Bir veritabanı işaretleme dili (.dbml) meta veri dosyasından Visual Basic veya C# kaynak kodu oluşturabilir. Bu yaklaşım uygulama eşleme kodu oluşturmadan önce varsayılan .dbml dosyasını özelleştirmek için bir fırsat sunar. Bu gelişmiş bir özelliktir.  
  
 Bu işlemdeki adımlar aşağıdaki gibidir:  
  
1.  Bir .dbml dosyası oluşturun.  
  
2.  .Dbml dosyasını değiştirmek için bir düzenleyici kullanın. .Dbml dosyanın şema tanımını (.xsd) dosyası için karşı doğrulamalısınız Not [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml dosyaları. Daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3.  Visual Basic veya C# kaynak kodu oluşturur.  
  
 Aşağıdaki örnekler SQLMetal komut satırı aracını kullanın. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, Northwind örnek veritabanından .dbml dosyası oluşturur. Veritabanı meta veriler için kaynak olarak veritabanının adını veya .mdf dosyasının adını kullanabilirsiniz.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, Visual Basic veya C# kaynak kodu dosyasının .dbml dosyasından oluşturur.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL’de Kod Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [SqlMetal.exe (Kod Üretme Aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
