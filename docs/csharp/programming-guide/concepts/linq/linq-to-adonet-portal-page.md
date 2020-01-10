---
title: ADO.NET'e LINQ (Portal Sayfası)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 84412e43a9d6b1e256e4ac8306a94126a3eaaaf4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635554"
---
# <a name="linq-to-adonet-portal-page"></a>ADO.NET'e LINQ (Portal Sayfası)
LINQ to ADO.NET, dil ile tümleşik sorgu (LINQ) programlama modelini kullanarak ADO.NET içinde herhangi bir sıralanabilir nesne üzerinde sorgulama yapmanızı sağlar.  
  
> [!NOTE]
> LINQ to ADO.NET belge .NET Framework SDK: [LINQ ve ADO.net](../../../../framework/data/adonet/linq-and-ado-net.md)' nin ADO.net bölümünde bulunur.  
  
 Üç ayrı ADO.NET dil ile tümleşik sorgu (LINQ) teknolojisi vardır: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]ve LINQ to Entities. LINQ to DataSet, <xref:System.Data.DataSet>daha zengin, iyileştirilmiş sorgulama sağlar [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server veritabanı şemalarını doğrudan sorgulayabilir ve LINQ to Entities varlık veri modeli sorgulamanızı sağlar.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 <xref:System.Data.DataSet>, ADO.NET ' deki en yaygın olarak kullanılan bileşenlerden biridir ve ADO.NET 'in üzerinde oluşturulduğu, bağlantısı kesilen programlama modelinin anahtar öğesidir. Ancak, bu da <xref:System.Data.DataSet>, sınırlı sayıda sorgu özelliğine sahip olmasına rağmen.  
  
 LINQ to DataSet, diğer birçok veri kaynağı için kullanılabilen aynı sorgu işlevini kullanarak <xref:System.Data.DataSet> daha zengin sorgu özellikleri oluşturmanızı sağlar.  
  
 Daha fazla bilgi için [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ilişkisel verileri nesne olarak yönetmeye yönelik bir çalışma zamanı altyapısı sağlar. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], bir ilişkisel veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeliyle eşlenir. Uygulamayı yürüttüğünüzde [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], nesne modelindeki dil ile tümleşik sorguları SQL 'e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], bunları işleyebileceğiniz nesnelere geri çevirir.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], veritabanında saklı yordamlar ve Kullanıcı tanımlı işlevler ve nesne modelinde devralma için destek içerir.  
  
 Daha fazla bilgi için bkz. [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 Varlık Veri Modeli, ilişkisel veriler .NET ortamında nesneler olarak sunulur. Bu, nesne katmanını LINQ desteği için ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden sorguları veritabanına göre formüllemesini sağlar. Bu yetenek LINQ to Entities olarak bilinir. Daha fazla bilgi için bkz. [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Dil ile tümleşik sorgu (LINQ) (C#)](./index.md)
