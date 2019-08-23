---
title: LINQ - SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 86c7e9fae270e75d1ba7e9725ded22ea1961311a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911995"
---
# <a name="linq-to-sql"></a>LINQ - SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ilişkisel verileri nesne olarak yönetmeye yönelik bir çalışma zamanı altyapısı sağlayan .NET Framework sürüm 3,5 bileşenidir.  
  
> [!NOTE]
> Ortak sütunlarda tabloları birbirleriyle ilişkilendiren, ilişkisel veriler iki boyutlu tabloların (*ilişkiler* veya *düz dosyalar*) bir koleksiyonu olarak görünür. Etkin bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şekilde kullanmak için, ilişkisel veritabanlarının temel ilkelerine bazı benzerlik sahibi olmanız gerekir.  
  
 ' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]De, bir ilişkisel veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeliyle eşleştirilir. Uygulama çalıştığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modelindeki dil ile tümleşik sorguları SQL 'e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bunları kendi programlama dilinizde birlikte çalışleyebileceğiniz nesnelere geri çevirir.  
  
 Visual Studio kullanan geliştiriciler genellikle ' nin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]birçok özelliğinin uygulanması için bir kullanıcı arabirimi sağlayan nesne ilişkisel Tasarımcısı kullanır.  
  
 Bu sürümünde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yer alan belgeler, uygulamalar oluşturmak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için ihtiyacınız olan temel yapı taşlarını, süreçlerini ve teknikleri açıklar. Ayrıca, belirli sorunlar için Microsoft Docs arayabilir ve uzmanlarla ayrıntılı olarak daha karmaşık konular tartışabilirsiniz [LINQ forumuna](https://go.microsoft.com/fwlink/?LinkId=76488)katılabilirsiniz. Son olarak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , [LINQ to SQL: ilişkisel veri teknik incelemesi için .NET dil tümleşik sorgusu](https://go.microsoft.com/fwlink/?LinkId=93205) , Visual Basic ve C# kod örnekleriyle birlikte tamamlanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 ' I kullanmaya [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]başlama hakkında [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bilgi ile birlikte daha dar bir genel bakış sağlar.  
  
 [Programlama Kılavuzu](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Eşleme, sorgulama, güncelleştirme, hata ayıklama ve benzer görevler için adımlar sağlar.  
  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 Uygulamasının [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]çeşitli yönleri hakkında başvuru bilgileri sağlar. Konular SQL-CLR türü eşlemesi, standart sorgu operatörü çevirisi ve daha fazlasını içerir.  
  
 [Örnekler](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Visual Basic ve C# örneklere bağlantılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Dil ile tümleşik sorgu (LINQ)-C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 ' De C#LINQ teknolojilerine genel bakış sağlar.
 
 [Dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Visual Basic ' de LINQ teknolojilerine genel bakış sağlar.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Visual Basic [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] kullanıcılarına yönelik teknolojiler açıklanmaktadır.  
  
 [LINQ ve ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 ADO.NET portalına bağlantı sağlar.  
  
 [LINQ to SQL Izlenecek yollar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 İçin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullanılabilen izlenecek yolları listeler.  
  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 Belgelerde kullanılan örnek veritabanlarının nasıl indirileceği açıklanır.  
  
 [LinqDataSource Web sunucusu denetimine genel bakış](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 ASP.NET veri kaynağı <xref:System.Web.UI.WebControls.LinqDataSource> denetim mimarisi [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] aracılığıyla denetimin Web geliştiricileri için nasıl kullanıma sunduğunu açıklar.
