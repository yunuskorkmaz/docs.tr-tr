---
title: "Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ff5a314fb4264f57f1db3e8475a2e3105897f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma #
İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], programlama diliniz nesne modelinde ilişkisel bir veritabanına eşlendi. İki araçları otomatik olarak oluşturmak için kullanılabilir bir [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] veya varolan bir veritabanını meta verilerden model C#.  
  
-   Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturmak için. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Oluşturmanıza yardımcı olmak için zengin bir kullanıcı arabirimi sağlayan bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli. Daha fazla bilgi için [LINQ-SQL Visual Studio Araçları](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
-   SQLMetal komut satırı aracıdır. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Var olan veritabanı ve bir nesne modeli oluşturmak için istediğiniz yoksa, nesne modeli kodunuzu kullanarak Düzenleyicisi oluşturabilirsiniz ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Daha fazla bilgi için bkz: [nasıl yapılır: dinamik olarak bir veritabanı oluşturmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Belgelerine [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] nasıl oluşturacağını örnekleri sağlar bir [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] veya kullanarak C# nesne modeli [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Aşağıdaki bilgileri SQLMetal komut satırı aracını kullanma örnekleri sağlayın. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği SQLMetal komut satırı üreten [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] kodu Northwind örnek veritabanı öznitelik tabanlı nesne modelini olarak. Saklı yordamları ve işlevleri de işlenir.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği SQLMetal komut satırında C# kod Northwind örnek veritabanı öznitelik tabanlı nesne modeli oluşturur. Saklı yordamları ve işlevleri de işlenir ve tablo adları otomatik olarak pluralized.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [LINQ to SQL nesne modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Öğrenme tarafından izlenecek yollar](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Nesne modeli oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
