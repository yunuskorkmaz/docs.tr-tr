---
title: "Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b28ff0bb8436fefc4956918889435e258ae98b12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama
Aşağıdaki örnek, statik bölümleme gerçekleştirir PLINQ için basit bir özel bölümleyici uygulamak için bir yol gösterir. Bölümleyici dinamik bölümleri desteklemiyor, gelen tüketilebilir değildir, çünkü <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Bu belirli bölümleyici speedup her öğe bir artan süreyi işleme gerektiren veri kaynakları için varsayılan aralığı bölümleyici sağlayabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Bu örnekte bölümleri her öğe için işleme süresi doğrusal bir artış varsayımına dayanır. Gerçek Hayatta, bu şekilde işleme sürelerini tahmin etmek zor olabilir. Statik bölümleyici belirli veri kaynağı ile kullanıyorsanız, bölümleme formülü kaynağı için en iyi duruma getirme, Yük Dengeleme mantığı ekleyebilir veya yaklaşım şekilde bölümleme bir öbek kullanmak [nasıl yapılır: dinamik bölümleri uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
