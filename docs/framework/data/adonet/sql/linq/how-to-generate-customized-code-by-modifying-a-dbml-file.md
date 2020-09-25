---
title: 'Nasıl yapılır: DBML Dosyasını Değiştirerek Özelleştirilmiş Kod Oluşturma'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: ab49f76a0d5e7338a93e21ae9a8d1d9d74a21e82
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173445"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Nasıl yapılır: DBML Dosyasını Değiştirerek Özelleştirilmiş Kod Oluşturma

Veritabanı biçimlendirme dili (. dbml) meta veri dosyasından Visual Basic veya C# kaynak kodu oluşturabilirsiniz. Bu yaklaşım, uygulama eşleme kodunu oluşturmadan önce default. dbml dosyasını özelleştirmek için bir fırsat sağlar. Bu gelişmiş bir özelliktir.  
  
 Bu işlemdeki adımlar aşağıdaki gibidir:  
  
1. Bir. dbml dosyası oluşturun.  
  
2. . Dbml dosyasını değiştirmek için bir düzenleyici kullanın. . Dbml dosyasının. dbml dosyaları için şema tanımı (. xsd) dosyasına göre doğrulanması gerektiğini unutmayın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Daha fazla bilgi için bkz. [LINQ to SQL kod oluşturma](code-generation-in-linq-to-sql.md).  
  
3. Visual Basic veya C# kaynak kodu oluşturun.  
  
 Aşağıdaki örneklerde SQLMetal komut satırı aracı kullanılır. Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, Northwind örnek veritabanından bir. dbml dosyası oluşturur. Veritabanı meta verileri için kaynak olarak, veritabanının adını veya. mdf dosyasının adını kullanabilirsiniz.  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, bir. dbml dosyasından Visual Basic veya C# kaynak kodu dosyası oluşturur.  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL’de Kod Oluşturma](code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
