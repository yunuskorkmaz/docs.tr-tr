---
title: ADO.NET'e LINQ (Portal Sayfası)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 84412e43a9d6b1e256e4ac8306a94126a3eaaaf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635554"
---
# <a name="linq-to-adonet-portal-page"></a>ADO.NET'e LINQ (Portal Sayfası)
LINQ to ADO.NET, Dil-Tümleşik Sorgu (LINQ) programlama modelini kullanarak ADO.NET herhangi bir sayısal nesne üzerinde sorgu yapmanızı sağlar.  
  
> [!NOTE]
> BELGELERI ADO.NET IÇIN LINQ .NET Framework SDK'nın ADO.NET bölümünde yer alır: [LINQ ve ADO.NET.](../../../../framework/data/adonet/linq-and-ado-net.md)  
  
 Üç ayrı ADO.NET Dil-Tümleşik Sorgu (LINQ) teknolojisi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]vardır: LinQ'dan DataSet'e ve LINQ'dan Varlıklara. LINQ to DataSet, <xref:System.Data.DataSet>SQL Server veritabanı şemalarını doğrudan sorgulamanızı [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sağlar ve LinQ'dan Varlıklara kadar daha zengin ve optimize edilmiş sorgulama sağlar ve Varlık Veri Modeli'ni sorgulamanızı sağlar.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 ADO.NET'da <xref:System.Data.DataSet> en yaygın olarak kullanılan bileşenlerden biridir ve ADO.NET üzerine inşa edildiği bağlantısız programlama modelinin önemli bir öğesidir. Ancak bu öneme rağmen, <xref:System.Data.DataSet> sorgu yetenekleri sınırlıdır.  
  
 LINQ to DataSet, diğer birçok veri kaynağı <xref:System.Data.DataSet> için kullanılabilen aynı sorgu işlevini kullanarak daha zengin sorgu özellikleri oluşturmanıza olanak tanır.  
  
 Daha fazla bilgi için [LinQ'dan DataSet'e](../../../../framework/data/adonet/linq-to-dataset.md)bakın.  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]ilişkisel verileri nesne olarak yönetmek için bir çalışma zamanı altyapısı sağlar. İlişkisel [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]bir veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeline eşlenir. Uygulamayı yürüttüğüzde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] nesne modelindeki dil tümleşik sorguları SQL'e çevirir ve yürütme için veritabanına gönderir. Veritabanı sonuçları döndürdüğünde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bunları işleyebileceğiniz nesnelere geri çevirir.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]veritabanında depolanan yordamlar ve kullanıcı tanımlı işlevler ve nesne modelinde devralma için destek içerir.  
  
 Daha fazla bilgi için [LINQ'dan SQL'e](../../../../framework/data/adonet/sql/linq/index.md)bakın.  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 Varlık Veri Modeli aracılığıyla, ilişkisel veriler .NET ortamında nesne olarak ortaya çıkarır. Bu, nesne katmanını LINQ desteği için ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden veritabanına karşı sorgular formüle etmesine olanak tanır. Bu özellik LinQ to Varlıklar olarak bilinir. Daha fazla bilgi [için LinQ to Varlıklar'a](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Dil-Tümleşik Sorgu (LINQ) (C#)](./index.md)
