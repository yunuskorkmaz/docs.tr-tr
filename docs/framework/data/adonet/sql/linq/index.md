---
title: LINQ - SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 78fbd1bde6727490e789ba22232af3f17af20d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql"></a>LINQ - SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]bir bileşeni olan [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ilişkisel veri nesneleri olarak yönetmek için bir çalışma zamanı altyapısı sağlar sürüm 3.5.  
  
> [!NOTE]
>  İlişkisel veri iki boyutlu tablolar koleksiyonu olarak görüntülenir (*ilişkileri* veya *düz dosyalar*), burada ortak sütunları tabloları birbirleri ile. Kullanılacak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] etkili bir şekilde ilişkisel veritabanları temel ilkeleri aşina olması gerekir.  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ilişkisel veritabanı veri modelinin Geliştirici programlama dilinde ifade nesne modeli eşlenir. Uygulama çalıştırıldığında [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL'e nesne modelinde dil ile tümleşik sorgu dönüşür ve yürütme için veritabanı gönderir. Veritabanı sonuçları döndürdüğünde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bunları kendi programlama dilinde çalışabilirsiniz nesnelere geri çevirir.  
  
 Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] genellikle [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], özelliklerinin çoğunu gerçekleştirmek için bir kullanıcı arabirimi sağlayan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Bu sürümünden belgelere [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] temel yapı taşlarının, işlemleri ve yapı için gereken teknikleri açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulamalar. Microsoft Docs belirli sorunları için arama da yapabilirsiniz ve katılabilirsiniz [LINQ Forumu](http://go.microsoft.com/fwlink/?LinkId=76488), uzmanlarıyla ayrıntılı daha karmaşık konular burada ele. Son olarak, [LINQ-SQL: ilişkisel veri .NET Language-Integrated sorgusu](http://go.microsoft.com/fwlink/?LinkId=93205) incelemeyi ayrıntıları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] teknolojisi ile tam [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ve C# kod örnekleri.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 Sıkıştırılmış bir bakış sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullanmaya başlama hakkında bilgi ile birlikte [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Programlama Kılavuzu](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Eşleme, sorgulama, güncelleştirme, hata ayıklama ve benzer görevler için adımlar sağlar.  
  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 Çeşitli yönleri hakkında başvuru bilgileri sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Konular SQL CLR türü eşleme, standart sorgu işleci çeviri ve daha fazlasını içerir.  
  
 [Örnekler](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Bağlantılar sağlar [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ve C# örnekleri.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Genel bir bakış sağlar [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] teknolojileri.  
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Açıklar [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] teknolojileri için [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] kullanıcılar.  
  
 [ADO.NET'e LINQ](http://msdn.microsoft.com/en-us/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 Bağlantılar için [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portal.  
  
 [LINQ-SQL izlenecek yollar](http://msdn.microsoft.com/en-us/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 İzlenecek yollar için kullanılabilir listeler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 Belgelerde kullanılan örnek veritabanları indirmek açıklar.  
  
 [LinqDataSource teknoloji genel bakış](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136)  
 Açıklar nasıl <xref:System.Web.UI.WebControls.LinqDataSource> kontrol çıkarır [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] aracılığıyla Web geliştiricileri için [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] veri kaynağı denetim mimarisi.
