---
title: 'Nasıl yapılır: Visual Basic veya içinde nesne modeli oluşturmaC#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 7d2c0600534c93f5884eec48a4bdaa3ce99945e9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002804"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Nasıl yapılır: Visual Basic veya C 'de nesne modeli oluşturma\#
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], kendi programlama dilinizdeki bir nesne modeli, ilişkisel bir veritabanıyla eşlenir. Varolan bir veritabanının meta verilerinden otomatik olarak bir Visual Basic veya C# model oluşturmak için iki araç mevcuttur.  
  
- Visual Studio kullanıyorsanız, bir nesne modeli oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz. O/R Tasarımcısı, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli oluşturmanıza yardımcı olmak için zengin bir kullanıcı arabirimi sağlar. Daha fazla bilgi için bkz. [Visual Studio 'Da LINQ to SQL araçları](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- SQLMetal komut satırı aracı. Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Mevcut bir veritabanınız yoksa ve bir nesne modelinden bir tane oluşturmak istiyorsanız, kod düzenleyicinizi ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A>kullanarak nesne modelinizi oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: dinamik olarak veritabanı oluşturma](how-to-dynamically-create-a-database.md).  
  
 O/R tasarımcısına yönelik belgeler, u/R tasarımcısını kullanarak bir Visual Basic veya C# nesne modeli oluşturma örneklerini sağlar. Aşağıdaki bilgiler, SQLMetal komut satırı aracının nasıl kullanılacağına ilişkin örnekler sağlar. Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının öznitelik tabanlı nesne modeli olarak Visual Basic kodu üretir. Saklı yordamlar ve işlevler de işlenir.  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının C# öznitelik tabanlı nesne modeli olarak kod üretir. Saklı yordamlar ve işlevler de işlenir ve tablo adları otomatik olarak plurar.  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide.md)
- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Öznitelik Tabanlı Eşleme](attribute-based-mapping.md)
- [SqlMetal.exe (Kod Üretme Aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Dış Eşleme](external-mapping.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
