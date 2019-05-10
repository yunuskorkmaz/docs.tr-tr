---
title: 'Nasıl yapılır: Bir dosyaya metin yazma'
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59b33c24c2821d0aef17f5feb67c1178810b939e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647780"
---
# <a name="how-to-write-text-to-a-file"></a>Nasıl yapılır: Bir dosyaya metin yazma
Bu konu, bir .NET uygulaması için bir dosyaya metin yazma için farklı yollar gösterir. 

Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:  
  
- <xref:System.IO.StreamWriter> zaman uyumlu olarak bir dosyaya yazmak için yöntemleri içerir (<xref:System.IO.StreamWriter.Write%2A> ve <xref:System.IO.TextWriter.WriteLine%2A>) veya zaman uyumsuz olarak (<xref:System.IO.StreamWriter.WriteAsync%2A> ve <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
- <xref:System.IO.File> metin gibi bir dosyaya yazmak için statik yöntemler sağlar <xref:System.IO.File.WriteAllLines%2A> ve <xref:System.IO.File.WriteAllText%2A>, veya gibi bir dosyaya metin eklenecek <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, ve <xref:System.IO.File.AppendText%2A>.  
  
- <xref:System.IO.Path> için dosya veya dizin yolu bilgileri olan strings olur. İçerdiği <xref:System.IO.Path.Combine%2A> yöntemi ve .NET Core 2.1 ve sonraki sürümlerinde, <xref:System.IO.Path.Join%2A> ve <xref:System.IO.Path.TryJoin%2A> izin veren birleştirme dizelerin bir dosya veya dizin yolu oluşturmak için yöntemleri.

> [!NOTE]
> Aşağıdaki örnekler yalnızca minimum gereken kod miktarını gösterir. Gerçek uygulama genelde daha sağlam hata denetimi ve özel durum işleme sağlar.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Örnek: Zaman uyumlu olarak StreamWriter ile metin yazma

Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.IO.StreamWriter> zaman uyumlu olarak metin aynı anda yeni bir dosya bir satıra yazmak için sınıf. Çünkü <xref:System.IO.StreamWriter> nesne bildirildi ve içinde örneklenen bir `using` deyimi <xref:System.IO.StreamWriter.Dispose%2A> yöntemi çağrılır, otomatik olarak boşaltır ve akışı kapatır.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a>Örnek: Zaman uyumlu olarak StreamWriter ile metin ekleme

Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.IO.StreamWriter> zaman uyumlu olarak metin ilk örnekte oluşturulan metin dosyasına eklenecek sınıf.   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Örnek: Zaman uyumsuz olarak StreamWriter ile metin yazma

Aşağıdaki örnek, zaman uyumsuz olarak yeni kullanarak bir dosyaya metin yazma işlemi gösterilmektedir <xref:System.IO.StreamWriter> sınıfı. Çağrılacak <xref:System.IO.StreamWriter.WriteAsync%2A> yöntem, yöntem çağrısının içinde olmalıdır bir `async` yöntemi. C# Örnek gerektirir C# 7.1 veya sonraki sürümü için destek ekler `async` programın giriş noktası değiştiricisi. 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Örnek: Yazma ve metin dosyası sınıfı ekleme

Aşağıdaki örnek, yeni bir dosyaya metin yazma ve kullanarak aynı dosya için yeni satırlık metin ekleme işlemi gösterilmektedir <xref:System.IO.File> sınıfı. <xref:System.IO.File.WriteAllText%2A> Ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri açın ve dosyayı otomatik olarak kapatın. Sağladığınız yolun, <xref:System.IO.File.WriteAllText%2A> yöntemi zaten var, dosyanın üzerine yazılır.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Nasıl yapılır: İçin bir yeni oluşturulan veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Nasıl yapılır: Açın ve bir günlük dosyasına Ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Nasıl yapılır: Bir dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)