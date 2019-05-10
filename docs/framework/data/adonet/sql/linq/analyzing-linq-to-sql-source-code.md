---
title: LINQ to SQL Kaynak Kodunu Analiz Etme
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 35bc4988b8b9845ce6f45bab6849cd4b53a858ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592479"
---
# <a name="analyzing-linq-to-sql-source-code"></a>LINQ to SQL Kaynak Kodunu Analiz Etme
Aşağıdaki adımları kullanarak, üretebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kaynak kodu Northwind örnek veritabanından. Karşılaştırabileceğiniz daha iyi nasıl farklı olan öğeleri görmek için veritabanı öğelerini nesne modeline öğeleriyle eşlendi.  
  
> [!NOTE]
>  Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Bu kod üretmek için.  
  
1. Geliştirme bilgisayarınızda Northwind örnek veritabanı yoksa, ücretsiz olarak indirebilirsiniz. Daha fazla bilgi için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2. Bir Visual Basic oluşturmak üzere SqlMetal komut satırı aracını kullanın veya C# kaynak dosyası. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Bir komut isteminde aşağıdaki komutları yazarak, Visual Basic oluşturabilir ve C# kaynak saklı yordamları ve işlevleri içeren dosyaları:  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
