---
title: LINQ-SQL kaynak kodunu analiz etme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e1677d8e30b083efe99f916b28672ddb6c3dd99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="analyzing-linq-to-sql-source-code"></a>LINQ-SQL kaynak kodunu analiz etme
Aşağıdaki adımları kullanarak, üretebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kaynak Northwind örnek veritabanı koddan. Karşılaştırabileceğiniz nesne modeli öğeleri daha iyi nasıl farklı öğeleri görmek için veritabanına öğelerin eşlendi.  
  
> [!NOTE]
>  Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] bu kodu oluşturmak için.  
  
1.  Northwind örnek veritabanı geliştirme bilgisayarınızda zaten yoksa, ücretsiz olarak karşıdan yükleyebilirsiniz. Daha fazla bilgi için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2.  Visual Basic veya C# kaynak dosyası oluşturmak üzere SqlMetal komut satırı aracını kullanın. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Bir komut isteminde aşağıdaki komutları yazarak, saklı yordamları ve işlevleri dahil Visual Basic ve C# kaynak dosyaları oluşturabilirsiniz:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Arka plan bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
