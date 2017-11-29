---
title: "Uzak vs. Yerel çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b04ba6dde572aa0a8edddc8a2a30a8e11a3e79c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="remote-vs-local-execution"></a>Uzak vs. Yerel çalıştırma
Sorgularınızın ya da uzaktan yürütme karar verebilirsiniz (diğer bir deyişle, veritabanı altyapısı veritabanında sorgu yürütür) veya yerel olarak ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel önbelleğe karşı sorgu yürütülür).  
  
## <a name="remote-execution"></a>Uzaktan yürütme  
 Aşağıdaki sorgu göz önünde bulundurun:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Veritabanınızı binlerce siparişleri satır varsa, bunları tüm küçük bir alt işlem almak istiyor musunuz. İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> uygulayan sınıf <xref:System.Linq.IQueryable> arabirimi. Bu yaklaşım sorgularını uzaktan çalıştırılabilir emin olur. Bu teknik akışından iki önemli faydası:  
  
-   Gereksiz verileri alınamadı.  
  
-   Veritabanı altyapısı tarafından çalıştırılan bir sorguyu genellikle daha büyük veritabanı dizinlerini nedeniyle verimli.  
  
## <a name="local-execution"></a>Yerel çalıştırma  
 Diğer durumlarda, yerel önbellekte eksiksiz ilgili varlıklar olarak sahip olmak isteyebilirsiniz. Bu amaçla <xref:System.Data.Linq.EntitySet%601> sağlar <xref:System.Data.Linq.EntitySet%601.Load%2A> tüm üyelerini açıkça yüklemek için yöntem <xref:System.Data.Linq.EntitySet%601>.  
  
 Varsa bir <xref:System.Data.Linq.EntitySet%601> yüklenen, zaten sonraki sorguları yerel olarak çalıştırılır. Bu yaklaşımın iki yolla yardımcı olur:  
  
-   Yerel olarak tamamını kullanılan veya birden çok kez, uzak sorgular ve ilişkili gecikmeleri önleyebilirsiniz.  
  
-   Varlık eksiksiz bir varlık olarak serileştirilebilir.  
  
 Aşağıdaki kod parçası nasıl yerel yürütme gösterilmektedir elde edilebilir:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Karşılaştırma  
 Güçlü bir seçenekleri birleşimini bu iki özellikleri sağlar: uzaktan yürütme büyük koleksiyonları ve yerel yürütme küçük koleksiyonlar için veya tam koleksiyon burada gereklidir. Uzaktan yürütme aracılığıyla uygulama <xref:System.Linq.IQueryable>ve bir bellek içi karşı yerel yürütme <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu. Yerel yürütme zorlamak için (diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601>), bkz: [bir tür için genel bir IEnumerable Dönüştür](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Sırasız kümeleri sorguları  
 Arabirimini uygulayan bir yerel koleksiyonu arasında önemli fark Not <xref:System.Collections.Generic.List%601> ve yürütülen uzak sorgularını sağlayan koleksiyonu *kümeleri sıralanmamış* ilişkisel bir veritabanındaki. <xref:System.Collections.Generic.List%601>Dizin değerlerini kullananlar gibi yöntemleri genellikle sırasız ayarlanmış bir uzak bir sorgu üzerinden alınamıyor listesi semantiği gerektirir. Bu nedenle, bu tür yöntemleri dolaylı olarak yük <xref:System.Data.Linq.EntitySet%601> yerel yürütülmesine izin vermek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
