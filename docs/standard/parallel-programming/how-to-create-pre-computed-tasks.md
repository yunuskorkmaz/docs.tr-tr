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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123133"
---
# <a name="how-to-create-pre-computed-tasks"></a>Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma
Bu belge, önbellekte tutulan eşenkron indirme işlemlerinin sonuçlarını almak için <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> yöntemin nasıl kullanılacağını açıklar. Yöntem, <xref:System.Threading.Tasks.Task.FromResult%2A> sağlanan <xref:System.Threading.Tasks.Task%601> değeri <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği olarak tutan bitmiş bir nesneyi döndürür. Bu yöntem, bir <xref:System.Threading.Tasks.Task%601> nesne döndüren bir eşyoklama işlemi gerçekleştirdiğinizde <xref:System.Threading.Tasks.Task%601> ve bu nesnenin sonucu zaten hesaplandığında yararlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizeleri web'den indirir. `DownloadStringAsync` Yöntemi tanımlar. Bu yöntem, dizeleri web'den eşzamanlı olarak indirir. Bu örnek, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> önceki işlemlerin sonuçlarını önbelleğe almak için bir nesne de kullanır. Giriş adresi bu önbellekte `DownloadStringAsync` tutulursa, <xref:System.Threading.Tasks.Task.FromResult%2A> içeriği bu <xref:System.Threading.Tasks.Task%601> adreste tutan bir nesne oluşturmak için yöntemi kullanır. Aksi `DownloadStringAsync` takdirde, dosyayı web'den indirir ve sonucu önbelleğe ekler.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Bu örnek, birden çok dizeleri iki kez indirmek için gereken süreyi hesaplamak. Sonuçlar önbellekte tutulduğundan, ikinci indirme işlemleri kümesi ilk kümeden daha az zaman almalıdır. Yöntem, <xref:System.Threading.Tasks.Task.FromResult%2A> yöntemin `DownloadStringAsync` bu <xref:System.Threading.Tasks.Task%601> önceden hesaplanmış sonuçları tutan nesneler oluşturmasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
