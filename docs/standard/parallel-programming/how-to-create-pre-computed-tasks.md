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
ms.openlocfilehash: 88f0782380d21858bc5dd0fc0fbf63bbf85403b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289999"
---
# <a name="how-to-create-pre-computed-tasks"></a>Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma
Bu belgede, <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> bir önbellekte tutulan zaman uyumsuz indirme işlemlerinin sonuçlarını almak için yönteminin nasıl kullanılacağı açıklanmaktadır. <xref:System.Threading.Tasks.Task.FromResult%2A>Yöntemi, <xref:System.Threading.Tasks.Task%601> özelliği olarak belirtilen değeri tutan tamamlanmış bir nesne döndürür <xref:System.Threading.Tasks.Task%601.Result%2A> . Bu yöntem, bir nesne döndüren zaman uyumsuz bir işlem gerçekleştirirken ve bu <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task%601> nesnenin sonucu zaten hesaplanmışsa yararlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek dizeleri Web 'den indirir. `DownloadStringAsync`Yöntemini tanımlar. Bu yöntem, dizeleri zaman uyumsuz olarak Web 'den indirir. Bu örnek <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , önceki işlemlerin sonuçlarını önbelleğe almak için de bir nesnesi kullanır. Giriş adresi bu önbellekte tutuluyorsa, bu `DownloadStringAsync` <xref:System.Threading.Tasks.Task.FromResult%2A> adresteki içeriği tutan bir nesne oluşturmak için yöntemini kullanır <xref:System.Threading.Tasks.Task%601> . Aksi takdirde, `DownloadStringAsync` dosyayı Web 'den indirir ve sonucu önbelleğe ekler.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Bu örnek, birden çok dizeyi iki kez indirmek için gereken zamanı hesaplar. İkinci indirme işlemleri kümesi, sonuçlar önbellekte tutulduğundan ilk ayarlanan süreden daha az zaman almalıdır. <xref:System.Threading.Tasks.Task.FromResult%2A>Yöntemi, `DownloadStringAsync` yönteminin <xref:System.Threading.Tasks.Task%601> Bu önceden hesaplanan sonuçları tutan nesneler oluşturmasına olanak sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev tabanlı zaman uyumsuz programlama](task-based-asynchronous-programming.md)
