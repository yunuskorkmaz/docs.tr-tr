---
title: ADO.NET'e LINQ (Portal Sayfası)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: b242a4153c46f00fbb3b80054426cf3c35bdfdc6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504129"
---
# <a name="linq-to-adonet-portal-page"></a>ADO.NET'e LINQ (Portal Sayfası)
ADO.NET'e LINQ kullanarak sorgulama ADO.NET içinde herhangi bir numaralandırma nesnesi üzerinden olanak tanır [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programlama modeli.  
  
> [!NOTE]
>  LINQ to ADO.NET belgeleri, ADO.NET .NET Framework SDK bölümünde bulunur: [LINQ ve ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Üç ayrı ADO.NET vardır [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] teknolojileri: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], ve [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. LINQ to DataSet sağlar üzerinden daha zengin, en iyi duruma getirilmiş sorgulama <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veritabanı şemalarını SQL Server, doğrudan sorgu sağlar ve [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] bir varlık veri modeli sorgu olanak tanır.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 <xref:System.Data.DataSet> ADO.NET en yaygın olarak kullanılan bileşenler biridir ve ADO.NET yerleşik olan bağlantısı kesilmiş programlama modelinin önemli bir öğedir. Bu teklifleriyle, ancak rağmen <xref:System.Data.DataSet> sorgu özellikleri sınırlıdır.  
  
 LINQ to DataSet daha zengin sorgu özellikleri oluşturmanızı sağlar <xref:System.Data.DataSet> diğer birçok veri kaynakları için sunulan sorgu işlevini kullanarak.  
  
 Daha fazla bilgi için [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] İlişkisel verileri nesne gibi yönetmek için bir çalışma zamanı altyapısı sağlar. İçinde [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], ilişkisel veritabanı veri modeli, geliştiricinin programlama dilinde ifade nesne modeli eşlenir. Uygulamayı çalıştırdığınızda [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dil ile tümleşik sorgu nesne modelinde SQL'e çevirir ve yürütme için veritabanı gönderir. Veritabanı sonuçları döndürdüğünde [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bunları yeniden düzenleyebilirsiniz nesnelerine çevirir.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] nesne modelinde devralma ve saklı yordamları ve kullanıcı tanımlı işlevleri veritabanında için destek içerir.  
  
 Daha fazla bilgi için [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 İlişkisel veri, varlık veri modeli .NET ortamını nesneler olarak kullanıma sunulur. Bu nesne için ideal bir hedef katman sağlar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] geliştiriciler, iş mantığı oluşturmak için kullanılan dil veritabanından karşı sorgular formüle etmek destek. Bu özellik olarak da bilinen [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. Bkz: [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) daha fazla bilgi için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Dil ile tümleşik sorgu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
