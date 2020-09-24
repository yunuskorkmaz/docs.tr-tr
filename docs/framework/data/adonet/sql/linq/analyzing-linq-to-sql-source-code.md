---
title: LINQ to SQL Kaynak Kodunu Analiz Etme
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: e39b1686269442044beb73bb7e572738832bec27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164590"
---
# <a name="analyzing-linq-to-sql-source-code"></a>LINQ to SQL Kaynak Kodunu Analiz Etme

Aşağıdaki adımları kullanarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Northwind örnek veritabanından kaynak kodu üretebilirsiniz. Farklı öğelerin nasıl eşleştirildiğini daha iyi görmek için nesne modeli öğelerini veritabanı öğeleriyle karşılaştırabilirsiniz.  
  
> [!NOTE]
> Visual Studio kullanan geliştiriciler, bu kodu oluşturmak için O/R tasarımcısını kullanabilir.  
  
1. Geliştirme bilgisayarınızda zaten Northwind örnek veritabanınız yoksa ücretsiz olarak indirebilirsiniz. Daha fazla bilgi için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).  
  
2. Visual Basic veya C# kaynak dosyası oluşturmak için SqlMetal komut satırı aracını kullanın. Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md). Komut istemine aşağıdaki komutları yazarak, saklı yordamları ve işlevleri içeren Visual Basic ve C# kaynak dosyaları oluşturabilirsiniz:  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](reference.md)
- [Arka Plan Bilgileri](background-information.md)
