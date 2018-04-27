---
title: LINQ-SQL kaynak kodunu analiz etme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 01191e36c71b2f6ac9844f6af2d57b1cb3ed2573
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="analyzing-linq-to-sql-source-code"></a>LINQ-SQL kaynak kodunu analiz etme
Aşağıdaki adımları kullanarak, üretebilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kaynak Northwind örnek veritabanı koddan. Karşılaştırabileceğiniz nesne modeli öğeleri daha iyi nasıl farklı öğeleri görmek için veritabanına öğelerin eşlendi.  
  
> [!NOTE]
>  Visual Studio kullanarak geliştiricileri kullanabilir [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] bu kodu oluşturmak için.  
  
1.  Northwind örnek veritabanı geliştirme bilgisayarınızda zaten yoksa, ücretsiz olarak karşıdan yükleyebilirsiniz. Daha fazla bilgi için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2.  Visual Basic veya C# kaynak dosyası oluşturmak üzere SqlMetal komut satırı aracını kullanın. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Bir komut isteminde aşağıdaki komutları yazarak, saklı yordamları ve işlevleri dahil Visual Basic ve C# kaynak dosyaları oluşturabilirsiniz:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
