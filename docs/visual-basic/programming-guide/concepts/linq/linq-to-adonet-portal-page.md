---
title: ADO.NET'e LINQ (Portal Sayfası)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 25ec71086d501e6ac9be22871563b0fb4e3cfb8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957576"
---
# <a name="linq-to-adonet-portal-page"></a>ADO.NET'e LINQ (Portal Sayfası)
LINQ to ADO.net, [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programlama modelini kullanarak ADO.NET içinde herhangi bir numaralandırılabilir nesneyi sorgulamanızı sağlar.  
  
> [!NOTE]
> LINQ to ADO.NET belgeleri .NET Framework SDK 'sının ADO.NET bölümünde bulunur: [LINQ ve ADO.net](../../../../framework/data/adonet/linq-and-ado-net.md).
  
 Üç ayrı ADO.net [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] teknolojisi vardır: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]ve LINQ to Entities. LINQ to DataSet üzerinde <xref:System.Data.DataSet>daha zengin, iyileştirilmiş sorgulama sağlar, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server veritabanı şemalarını doğrudan sorgulayabilir ve LINQ to Entities varlık veri modeli sorgulamanızı sağlar.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 , <xref:System.Data.DataSet> ADO.net ' deki en yaygın olarak kullanılan bileşenlerden biridir ve ADO.net 'in üzerinde oluşturulduğu, bağlantısı kesilen programlama modelinin temel öğesidir. Ancak, bu kadar belirgin olsa da, <xref:System.Data.DataSet> sınırlı sorgu yeteneklerine sahiptir.  
  
 LINQ to DataSet, diğer birçok veri kaynağı için kullanılabilen aynı <xref:System.Data.DataSet> sorgu işlevini kullanarak ' ye daha zengin sorgu özellikleri oluşturmanızı sağlar.  
  
 Daha fazla bilgi için [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]ilişkisel verileri nesne olarak yönetmeye yönelik bir çalışma zamanı altyapısı sağlar. ' [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]De, bir ilişkisel veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeliyle eşleştirilir. Uygulamayı yürüttüğünüzde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] nesne modelindeki dil ile tümleşik sorguları SQL 'e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bunları işleyebileceğiniz nesnelere geri çevirir.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], veritabanında saklı yordamlar ve Kullanıcı tanımlı işlevler ve nesne modelinde devralma için destek içerir.  
  
 Daha fazla bilgi için bkz. [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 Varlık Veri Modeli, ilişkisel veriler .NET ortamında nesneler olarak sunulur. Bu, nesne katmanını destek için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden sorguları veritabanına göre formüllemesini sağlar. Bu yetenek LINQ to Entities olarak bilinir. Daha fazla bilgi için bkz. [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
