---
title: 'Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091528"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama
Aşağıdaki örnek, statik bölümleme gerçekleştiren PLINQ için basit bir özel bölümleyici uygulamak için bir yol gösterir. Bölümleyici dinamik bölümleri desteklemediği için, 'den <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>tüketilemez. Bu özel bölümleyici, her öğenin artan miktarda işlem süresi gerektirdiği veri kaynakları için varsayılan aralık bölümleyicisi üzerinden hız sağlayabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Bu örnekteki bölümler, her öğe için işleme süresinde doğrusal bir artış varsayımına dayanır. Gerçek dünyada, bu şekilde işlem sürelerini tahmin etmek zor olabilir. Belirli bir veri kaynağına sahip statik bir bölümleyici kullanıyorsanız, kaynak için bölümleme formülü optimize edebilir, yük dengeleme mantığı ekleyebilir veya [Dinamik Bölümleri Uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)' da gösterildiği gibi bir yığın bölümleme yaklaşımı kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
