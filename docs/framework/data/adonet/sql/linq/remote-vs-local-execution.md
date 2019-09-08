---
title: Uzak ve Yerel Yürütme Karşılaştırması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: a21d5bbffdb1a78d3062929a1ca384a750af59a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781161"
---
# <a name="remote-vs-local-execution"></a>Uzak ve Yerel Yürütme Karşılaştırması
Sorgularınızı uzaktan yürütmeye karar verebilirsiniz (yani, veritabanı altyapısı sorguyu veritabanına karşı yürütür) veya yerel olarak ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguyu yerel bir önbellekte yürütür).  
  
## <a name="remote-execution"></a>Uzaktan Yürütme  
 Aşağıdaki sorguyu göz önünde bulundurun:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Veritabanınızda binlerce sipariş satırı varsa, küçük bir alt kümeyi işlemeye kadar tümünü almak istemezsiniz. ' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.IQueryable> sınıfı arabirimini uygular. <xref:System.Data.Linq.EntitySet%601> Bu yaklaşım, bu tür sorguların uzaktan yürütülmesini sağlar. Bu teknikten iki önemli avantaj akışı:  
  
- Gereksiz veriler alınmadı.  
  
- Veritabanı altyapısı tarafından yürütülen bir sorgu, veritabanı dizinleri nedeniyle genellikle daha etkilidir.  
  
## <a name="local-execution"></a>Yerel Yürütme Karşılaştırması  
 Diğer durumlarda, yerel önbellekte ilgili varlıkların tamamen kümesine sahip olmak isteyebilirsiniz. Bu amaçla <xref:System.Data.Linq.EntitySet%601> , tümüyelerini<xref:System.Data.Linq.EntitySet%601.Load%2A> açıkça yüklemek için yöntemini sağlar. <xref:System.Data.Linq.EntitySet%601>  
  
 <xref:System.Data.Linq.EntitySet%601> Zaten yüklüyse, sonraki sorgular yerel olarak yürütülür. Bu yaklaşım iki şekilde yardımcı olur:  
  
- Tamamlanma kümesinin yerel olarak veya birden çok kez kullanılması gerekiyorsa, uzak sorgulardan ve ilişkili gecikmelerin önüne kurtulabilirsiniz.  
  
- Varlık, bir bütün varlık olarak seri hale getirilebilir.  
  
 Aşağıdaki kod parçası, yerel yürütmenin nasıl elde edilebilir olduğunu gösterir:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Karşılaştırma  
 Bu iki özellik, seçeneklerin güçlü bir birleşimini sağlar: büyük koleksiyonlar için uzaktan yürütme ve küçük koleksiyonlar için yerel yürütme ve tüm koleksiyonun gerekli olduğu durumlar. Uzaktan yürütmeyi, bellek <xref:System.Linq.IQueryable> <xref:System.Collections.Generic.IEnumerable%601> içi bir koleksiyon ile ve yerel yürütme aracılığıyla uyguırın. Yerel yürütmeyi zorlamak için (yani, <xref:System.Collections.Generic.IEnumerable%601>) bkz. [bir türü genel IEnumerable 'a dönüştürme](convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Sırasız kümeler için sorgular  
 ' İ uygulayan <xref:System.Collections.Generic.List%601> bir yerel koleksiyon ve ilişkisel bir veritabanındaki *sırasız kümeler* için yürütülen uzak sorgular sağlayan bir koleksiyon arasındaki önemli farkı unutmayın. <xref:System.Collections.Generic.List%601>Dizin değerlerini kullanan Yöntemler, genellikle sıralanmamış bir küme için uzak bir sorgu üzerinden elde edilemez liste semantiğini gerektirir. Bu nedenle, bu tür yöntemler yerel yürütmeye izin <xref:System.Data.Linq.EntitySet%601> vermek için öğesini örtülü olarak yükler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
