---
title: 'Nasıl yapılır: DBML dosyasını değiştirerek özelleştirilmiş kod oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: dccef2af3d13099b71d3ea8418242e5a5cc16ae5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
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
