---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: b0660312f540a69911905edd08541ed70cf39bb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174322"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].NET Framework sürüm 3.5'in bir bileşenidir ve ilişkisel verileri nesne olarak yönetmek için çalışma zamanı altyapısı sağlar.  
  
> [!NOTE]
> İlişkisel veriler, ortak sütunların tabloların birbiriyle ilişkili olduğu iki boyutlu tablolar *(ilişkiler* veya *düz dosyalar)* topluluğu olarak görünür. Etkili [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir şekilde kullanmak için, ilişkisel veritabanlarının temel ilkelerine aşina olmalısınız.  
  
 İlişkisel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]bir veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeline eşlenir. Uygulama çalıştığında, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modelindeki dil tümleşik sorguları SQL'e çevirir ve bunları yürütme için veritabanına gönderir. Veritabanı sonuçları döndürdüğünde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bunları kendi programlama dilinizde çalışabileceğiniz nesnelere geri çevirir.  
  
 Visual Studio kullanan geliştiriciler genellikle nesne ilişkisel tasarımcı, hangi özelliklerinin birçok uygulamak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]için bir kullanıcı arabirimi sağlar kullanın.  
  
 Bu sürümde yer alan belgeler, uygulama oluşturma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için gereken temel yapı taşlarını, süreçleri ve teknikleri açıklar. Ayrıca belirli sorunlar için Microsoft Dokümanları'nda arama yapabilir ve daha karmaşık konuları uzmanlarla ayrıntılı olarak tartışabileceğiniz [LINQ Forumu'na](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)katılabilirsiniz. Son olarak, [LINQ'dan SQL'e: .NET Dil-İlişkisel Veri için Tümleşik Sorgu](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) teknik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bilgileri, Visual Basic ve C# kod örnekleri ile birlikte.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](getting-started.md)  
 Kullanmaya [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nasıl başlandığına ilişkin bilgilerle birlikte yoğunlaştırılmış bir genel bakış sağlar.  
  
 [Programlama Kılavuzu](programming-guide.md)  
 Eşleme, sorgulama, güncelleştirme, hata ayıklama ve benzeri görevler için adımlar sağlar.  
  
 [Başvuru](reference.md)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Çeşitli yönleri hakkında referans bilgileri sağlar. Konular arasında SQL-CLR Türü Eşleme, Standart Sorgu Operatörü Çevirisi ve daha fazlası yer almaktadır.  
  
 [Örnekler](samples.md)  
 Visual Basic ve C# örneklerine bağlantılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Dil-Entegre Sorgu (LINQ) - C #](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 C#'daki LINQ teknolojilerine genel bakış sağlar.

 [Dil-Entegre Sorgu (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Visual Basic'te LINQ teknolojilerine genel bakış sağlar.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Visual Basic kullanıcıları için LINQ teknolojilerini açıklar.  
  
 [LINQ ve ADO.NET](../../linq-and-ado-net.md)  
 ADO.NET portalına bağlantılar.  
  
 [LINQ 'dan SQL Walkthroughs'a](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Için kullanılabilir gözden [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]geçirme leri listeler.  
  
 [Örnek Veritabanları İndirme](downloading-sample-databases.md)  
 Belgelerde kullanılan örnek veritabanlarının nasıl indirilen açıklanır.  
  
 [LinqDataSource Web Sunucusu Kontrolüne Genel Bakış](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Denetimin, <xref:System.Web.UI.WebControls.LinqDataSource> veri kaynağı denetim mimarisiASP.NET aracılığıyla Web geliştiricilere Dil Tümleşik Sorgusunu (LINQ) nasıl ifşa ettiğini açıklar.
