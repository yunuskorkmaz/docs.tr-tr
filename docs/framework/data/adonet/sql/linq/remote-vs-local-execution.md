---
title: Uzak ve Yerel Yürütme Karşılaştırması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: a25186f6283f01ef56b1c684c4a43b9a60fb6d64
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619675"
---
# <a name="remote-vs-local-execution"></a>Uzak ve Yerel Yürütme Karşılaştırması
Sorgularınızın ya da uzaktan yürütün karar verebilirsiniz (diğer bir deyişle, veritabanı altyapısı veritabanı sorgusu çalıştırır) veya yerel olarak ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel önbelleğe karşı sorgu yürütülür).  
  
## <a name="remote-execution"></a>Uzaktan Yürütme  
 Şu sorguyu inceleyin:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Veritabanınızı gösteren binlerce satır siparişler varsa, bunların tüm küçük bir alt işleme alınması istemezsiniz. İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> sınıfının Implements <xref:System.Linq.IQueryable> arabirimi. Bu yaklaşım sorgularını uzaktan yürütüldüğünden emin olur. Bu teknik akıştan iki önemli avantajları:  
  
- Gereksiz verileri alınamadı.  
  
- Veritabanı altyapısı tarafından çalıştırılan bir sorgu genellikle büyük verimli veritabanı dizinleri nedeniyle.  
  
## <a name="local-execution"></a>Yerel Yürütme Karşılaştırması  
 Diğer durumlarda, ilişkili varlık kümesinin tamamını yerel önbellek üzerinde olmasını isteyebilirsiniz. Bu amaçla <xref:System.Data.Linq.EntitySet%601> sağlar <xref:System.Data.Linq.EntitySet%601.Load%2A> tüm üyelerini açıkça yüklemek için gereken yöntemini <xref:System.Data.Linq.EntitySet%601>.  
  
 Varsa bir <xref:System.Data.Linq.EntitySet%601> zaten yüklendiğinde sonraki sorgular yerel olarak çalıştırılır. Bu yaklaşım, iki şekilde yardımcı olur:  
  
- Tam bir set yerel olarak kullanılması gerekir ya da birden çok kez uzak sorguları ve ilişkili gecikme süreleri önleyebilirsiniz.  
  
- Varlık eksiksiz bir varlık seri hale getirilebilir.  
  
 Aşağıdaki kod parçası yerel yürütme gösterilmektedir elde edilebilir:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Karşılaştırma  
 Bu iki özellik güçlü bir birleşim seçenekleri sağlar: büyük ve küçük koleksiyonlar için veya tam koleksiyon gerekmesi halinde yerel yürütme için uzaktan yürütme. Uzaktan yürütme aracılığıyla uygulama <xref:System.Linq.IQueryable>ve bellek içi karşı yerel yürütme <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu. Yerel yürütme zorlamak için (diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601>), bkz: [türü genel IEnumerable öğesine dönüştürme](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Sırasız kümeleri sorguları  
 Uygulayan bir yerel koleksiyonu arasındaki önemli fark Not <xref:System.Collections.Generic.List%601> ve uzak sorguları karşı yürütülen sağlayan koleksiyonu *kümeleri sıralanmamış* ilişkisel bir veritabanındaki. <xref:System.Collections.Generic.List%601> Dizin değerlerinin kullananlar gibi yöntemler, genellikle bir sıralanmamış karşı uzak sorgu alınamıyor listesi semantiğini gerektirir. Bu nedenle, bu tür yöntemler dolaylı olarak yük <xref:System.Data.Linq.EntitySet%601> yerel yürütmeye olanak tanımak için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
