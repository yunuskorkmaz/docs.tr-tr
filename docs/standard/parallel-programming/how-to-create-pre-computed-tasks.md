---
title: 'Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: f5d2a70685fe0401d0219b99ada6936ac04691f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123133"
---
# <a name="how-to-create-pre-computed-tasks"></a>Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma
Bu belgede, bir önbellekte tutulan zaman uyumsuz indirme işlemlerinin sonuçlarını almak için <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> yönteminin nasıl kullanılacağı açıklanmaktadır. <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemi, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği olarak belirtilen değeri tutan bir tamamlanmış <xref:System.Threading.Tasks.Task%601> nesnesi döndürür. Bu yöntem, bir <xref:System.Threading.Tasks.Task%601> nesnesi döndüren zaman uyumsuz bir işlem gerçekleştirirken ve bu <xref:System.Threading.Tasks.Task%601> nesnesinin sonucu zaten hesaplanmışsa yararlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek dizeleri Web 'den indirir. `DownloadStringAsync` yöntemini tanımlar. Bu yöntem, dizeleri zaman uyumsuz olarak Web 'den indirir. Bu örnek, önceki işlemlerin sonuçlarını önbelleğe almak için de bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> nesnesi kullanır. Giriş adresi bu önbellekte tutuluyorsa `DownloadStringAsync`, bu adresteki içeriği tutan bir <xref:System.Threading.Tasks.Task%601> nesnesi oluşturmak için <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemini kullanır. Aksi takdirde, `DownloadStringAsync` dosyayı Web 'den indirir ve sonucu önbelleğe ekler.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Bu örnek, birden çok dizeyi iki kez indirmek için gereken zamanı hesaplar. İkinci indirme işlemleri kümesi, sonuçlar önbellekte tutulduğundan ilk ayarlanan süreden daha az zaman almalıdır. <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemi, `DownloadStringAsync` yönteminin önceden hesaplanan bu sonuçları tutan <xref:System.Threading.Tasks.Task%601> nesneleri oluşturmasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
