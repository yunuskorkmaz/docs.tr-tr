---
title: 'Nasıl yapılır: Önceden hesaplanan görevler oluşturma'
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
ms.openlocfilehash: aa95eccfa39073bb8ccb3cb9c49e099ac1f90ab1
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222112"
---
# <a name="how-to-create-pre-computed-tasks"></a>Nasıl yapılır: Önceden hesaplanan görevler oluşturma
Bu belgenin nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> zaman uyumsuz indirme işlemlerinin bir ön bellekte tutulan sonuçlarını almak için yöntemi. <xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi döndürür bir tamamlanmış <xref:System.Threading.Tasks.Task%601> olarak sağlanan değeri tutan bir nesne kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği. Döndüren zaman uyumsuz bir işlem gerçekleştirdiğinizde bu yöntem kullanışlıdır bir <xref:System.Threading.Tasks.Task%601> nesne ve bu sonucu <xref:System.Threading.Tasks.Task%601> nesne zaten hesaplanmışsa.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizeleri Web'den indirir. Tanımladığı `DownloadStringAsync` yöntemi. Bu yöntem, dizeleri zaman uyumsuz olarak Web'den indirir. Bu örnekte ayrıca bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> önceki işlemlerinin sonuçlarını önbelleğe almak için nesne. Giriş adresi bu önbellekte tutulan varsa `DownloadStringAsync` kullanan <xref:System.Threading.Tasks.Task.FromResult%2A> üretmek için yöntemi bir <xref:System.Threading.Tasks.Task%601> adreste içeriğini tutan nesne. Aksi takdirde, `DownloadStringAsync` dosyayı Web'den indirir ve önbelleğe sonucu ekler.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Bu örnek, birden çok dizeyi iki kez indirmek için gereken süreyi hesaplar. Sonuçları önbellekte tutulan olduğundan ikinci indirme işlemlerinin kümesini ilk süreden daha kısa zamanda almanız gerekir. <xref:System.Threading.Tasks.Task.FromResult%2A> Yöntemi etkinleştirir `DownloadStringAsync` yöntemini <xref:System.Threading.Tasks.Task%601> bu tutun nesneleri önceden hesaplanan sonuçlar.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesine yapıştırın veya adlı bir dosyaya yapıştırın `CachedDownloads.cs` (`CachedDownloads.vb` Visual Basic için), ve ardından Geliştirici komut istemi penceresi Visual Studio için aşağıdaki komutu çalıştırın.  
  
 Visual C#  
  
 **csc.exe CachedDownloads.cs**  
  
 Visual Basic  
  
 **Vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
