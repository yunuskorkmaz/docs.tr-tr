---
title: 'Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: e2491cf18be556cb26f084a178b7bf09448c6904
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546620"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Nasıl yapılır: Visual Basic veya C 'de nesne modeli oluşturma\#
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, kendi programlama dilinizdeki bir nesne modeli, ilişkisel bir veritabanıyla eşlenir. Varolan bir veritabanının meta verilerinden otomatik olarak bir Visual Basic veya C# modeli oluşturmak için iki araç mevcuttur.  
  
- Visual Studio kullanıyorsanız, bir nesne modeli oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz. O/R Tasarımcısı, nesne modeli oluşturmanıza yardımcı olmak için zengin bir kullanıcı arabirimi sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Daha fazla bilgi için bkz. [Visual Studio 'Da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- SQLMetal komut satırı aracı. Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Mevcut bir veritabanınız yoksa ve bir nesne modelinden bir tane oluşturmak istiyorsanız, kod düzenleyicinizi ve ' yi kullanarak nesne modelinizi oluşturabilirsiniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: dinamik olarak veritabanı oluşturma](how-to-dynamically-create-a-database.md).  
  
 O/R tasarımcısına yönelik belgeler, u/R tasarımcısını kullanarak Visual Basic veya C# nesne modeli oluşturma örneklerini sağlar. Aşağıdaki bilgiler, SQLMetal komut satırı aracının nasıl kullanılacağına ilişkin örnekler sağlar. Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının öznitelik tabanlı nesne modeli olarak Visual Basic kodu üretir. Saklı yordamlar ve işlevler de işlenir.  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterilen SQLMetal komut satırı, Northwind örnek veritabanının öznitelik tabanlı nesne modeli olarak C# kodu üretir. Saklı yordamlar ve işlevler de işlenir ve tablo adları otomatik olarak plurar.  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu](programming-guide.md)
- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
- [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Öznitelik Tabanlı Eşleme](attribute-based-mapping.md)
- [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Dış Eşleme](external-mapping.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
