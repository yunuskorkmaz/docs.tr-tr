---
title: LINQ - SQL
description: LINQ to SQL, ilişkisel verileri nesne olarak yönetmeye yönelik bir çalışma zamanı altyapısı sağlayan .NET Framework bileşenidir.
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: d6fadecf17cae21527cec2180b6d6c5b5e85d0cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551320"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , ilişkisel verileri nesne olarak yönetmeye yönelik bir çalışma zamanı altyapısı sağlayan .NET Framework sürüm 3,5 bileşenidir.  
  
> [!NOTE]
> Ortak sütunlarda tabloları birbirleriyle ilişkilendiren, ilişkisel veriler iki boyutlu tabloların (*ilişkiler* veya *düz dosyalar*) bir koleksiyonu olarak görünür. Etkin bir şekilde kullanmak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , ilişkisel veritabanlarının temel ilkelerine bazı benzerlik sahibi olmanız gerekir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, bir ilişkisel veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeliyle eşleştirilir. Uygulama çalıştığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modelindeki dil ile tümleşik SORGULARı SQL 'e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bunları kendi programlama dilinizde birlikte çalışleyebileceğiniz nesnelere geri çevirir.  
  
 Visual Studio kullanan geliştiriciler genellikle ' nin birçok özelliğinin uygulanması için bir kullanıcı arabirimi sağlayan Nesne İlişkisel Tasarımcısı kullanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 Bu sürümünde yer alan belgeler, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar oluşturmak için ihtiyacınız olan temel yapı taşlarını, süreçlerini ve teknikleri açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Ayrıca, belirli sorunlar için Microsoft Docs arayabilir ve uzmanlarla ayrıntılı olarak daha karmaşık konular tartışabilirsiniz [LINQ forumuna](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)katılabilirsiniz. Son olarak, [LINQ to SQL: Ilişkisel veri teknik incelemesi için .NET dil tümleşik sorgusu](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , Visual Basic ve C# kod örnekleriyle birlikte tamamlanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](getting-started.md)  
 ' I [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullanmaya başlama hakkında bilgi ile birlikte daha dar bir genel bakış sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 [Programlama Kılavuzu](programming-guide.md)  
 Eşleme, sorgulama, güncelleştirme, hata ayıklama ve benzer görevler için adımlar sağlar.  
  
 [Başvuru](reference.md)  
 Uygulamasının çeşitli yönleri hakkında başvuru bilgileri sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Konular SQL-CLR türü eşlemesi, standart sorgu operatörü çevirisi ve daha fazlasını içerir.  
  
 [Örnekler](samples.md)  
 Visual Basic ve C# örneklerine bağlantılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Dil ile tümleşik sorgu (LINQ)-C #](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 C# dilinde LINQ teknolojilerine genel bakış sağlar.

 [Dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Visual Basic ' de LINQ teknolojilerine genel bakış sağlar.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Visual Basic kullanıcılarına yönelik LINQ teknolojilerini açıklar.  
  
 [LINQ ve ADO.NET](../../linq-and-ado-net.md)  
 ADO.NET portalına bağlantı sağlar.  
  
 [LINQ to SQL Izlenecek yollar](/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 İçin kullanılabilen izlenecek yolları listeler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 [Örnek Veritabanları İndirme](downloading-sample-databases.md)  
 Belgelerde kullanılan örnek veritabanlarının nasıl indirileceği açıklanır.  
  
 [LinqDataSource Web sunucusu denetimine genel bakış](/previous-versions/aspnet/bb547113(v=vs.100))  
 <xref:System.Web.UI.WebControls.LinqDataSource>ASP.NET veri kaynağı denetim mimarisi aracılığıyla denetimin Web geliştiricilerine dil Ile tümleşik sorgu (LINQ) nasıl kullanıma sunduğunu açıklar.
