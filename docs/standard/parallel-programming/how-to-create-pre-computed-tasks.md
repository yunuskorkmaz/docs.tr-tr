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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e68465b6fae39089600457414e7f2a2328f725b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593129"
---
# <a name="how-to-create-pre-computed-tasks"></a>Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma
Bu belgenin nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> zaman uyumsuz indirme işlemlerinin bir ön bellekte tutulan sonuçlarını almak için yöntemi. <xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi döndürür bir tamamlanmış <xref:System.Threading.Tasks.Task%601> olarak sağlanan değeri tutan bir nesne kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği. Döndüren zaman uyumsuz bir işlem gerçekleştirdiğinizde bu yöntem kullanışlıdır bir <xref:System.Threading.Tasks.Task%601> nesne ve bu sonucu <xref:System.Threading.Tasks.Task%601> nesne zaten hesaplanmışsa.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizeleri Web'den indirir. Tanımladığı `DownloadStringAsync` yöntemi. Bu yöntem, dizeleri zaman uyumsuz olarak Web'den indirir. Bu örnekte ayrıca bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> önceki işlemlerinin sonuçlarını önbelleğe almak için nesne. Giriş adresi bu önbellekte tutulan varsa `DownloadStringAsync` kullanan <xref:System.Threading.Tasks.Task.FromResult%2A> üretmek için yöntemi bir <xref:System.Threading.Tasks.Task%601> adreste içeriğini tutan nesne. Aksi takdirde, `DownloadStringAsync` dosyayı Web'den indirir ve önbelleğe sonucu ekler.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Bu örnek, birden çok dizeyi iki kez indirmek için gereken süreyi hesaplar. Sonuçları önbellekte tutulan olduğundan ikinci indirme işlemlerinin kümesini ilk süreden daha kısa zamanda almanız gerekir. <xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi etkinleştirir `DownloadStringAsync` yöntemini <xref:System.Threading.Tasks.Task%601> bu tutun nesneleri önceden hesaplanan sonuçlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
