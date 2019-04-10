---
title: 'Nasıl yapılır: DBML Dosyasını Değiştirerek Özelleştirilmiş Kod Oluşturma'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: c3fa4d9db4076309ab7d6066cc7072797eaead54
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338429"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Nasıl yapılır: DBML Dosyasını Değiştirerek Özelleştirilmiş Kod Oluşturma
Visual Basic oluşturabilir veya C# kaynak koddan bir veritabanı işaretleme dili (.dbml) meta veri dosyası. Bu yaklaşım, varsayılan .dbml dosyası uygulama eşlemesi kodu oluşturmadan önce özelleştirmek için bir fırsat sağlar. Bu gelişmiş bir özelliktir.  
  
 Bu işlemdeki adımlar aşağıdaki gibidir:  
  
1. Bir .dbml dosyası oluşturun.  
  
2. Bir .dbml dosyası değiştirmek için bir düzenleyici kullanın. Bir .dbml dosyası için şema tanımı (.xsd) dosyası karşı doğrulamalıdır Not [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml dosyaları. Daha fazla bilgi için [LINQ to SQL'de kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3. Visual Basic oluşturmak veya C# kaynak kodu.  
  
 Aşağıdaki örnekler SQLMetal komut satırı aracını kullanın. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, Northwind örnek veritabanındaki bir .dbml dosyası oluşturur. Veritabanı meta veri kaynağı olarak veritabanı adını veya .mdf dosyası adını kullanabilirsiniz.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod Visual Basic oluşturur veya C# bir .dbml dosyasından kaynak kodu dosyası.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL’de Kod Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (Kod Üretme Aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
