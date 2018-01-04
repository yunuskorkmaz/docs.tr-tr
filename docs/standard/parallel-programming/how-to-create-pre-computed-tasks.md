---
title: "Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 262aa626e9e426da94de0d2ad5f2ef04a5bbc5f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-pre-computed-tasks"></a>Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma
Bu belge nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> önbellekte tutulur zaman uyumsuz indirme işlemlerinin sonuçlarını alma yöntemi. <xref:System.Threading.Tasks.Task.FromResult%2A> Yöntem bir tamamlanmış <xref:System.Threading.Tasks.Task%601> olarak sağlanan değer tutan nesnenin kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği. Döndüren zaman uyumsuz bir işlem gerçekleştirdiğinizde bu yöntem kullanışlıdır bir <xref:System.Threading.Tasks.Task%601> nesne ve bu sonucu <xref:System.Threading.Tasks.Task%601> nesne zaten hesaplanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek dizeleri Web'den indirir. Tanımladığı `DownloadStringAsync` yöntemi. Bu yöntem dizeleri web üzerinden zaman uyumsuz olarak yükler. Bu örnek ayrıca kullanan bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> önceki işlemlerinin sonuçlarını önbelleğe almak için nesne. Bu önbellek, giriş adresi tutulursa `DownloadStringAsync` kullanır <xref:System.Threading.Tasks.Task.FromResult%2A> üretmek için yöntemi bir <xref:System.Threading.Tasks.Task%601> bu adresinde içeriğini tutan nesne. Aksi takdirde `DownloadStringAsync` web sunucusundan dosya indirir ve önbelleğe sonuç ekler.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Bu örnekte, iki kez birden çok dizenin indirmek için gereken süreyi hesaplar. Sonuçları önbellekte tutulur çünkü indirme işlemleri ikinci kümesi ilk kümesi'den daha az zaman almanız gerekir. <xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi etkinleştirir `DownloadStringAsync` oluşturmak için yöntemi <xref:System.Threading.Tasks.Task%601> bunlar tutun nesneleri önceden hesaplanan sonuçları.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `CachedDownloads.cs` (`CachedDownloads.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
