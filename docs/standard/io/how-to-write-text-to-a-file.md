---
title: 'Nasıl yapılır: bir dosyaya metin yazma'
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
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160254"
---
# <a name="how-to-write-text-to-a-file"></a>Nasıl yapılır: bir dosyaya metin yazma
Bu konu başlığı altında, bir .NET uygulaması için bir dosyaya metin yazmanın farklı yolları gösterilmektedir.

Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:  
  
- <xref:System.IO.StreamWriter>, bir dosyaya (<xref:System.IO.StreamWriter.Write%2A> ve <xref:System.IO.TextWriter.WriteLine%2A>) ya da zaman uyumsuz (<xref:System.IO.StreamWriter.WriteAsync%2A> ve <xref:System.IO.StreamWriter.WriteLineAsync%2A>) yazma yöntemlerini içerir.  
  
- <xref:System.IO.File>, <xref:System.IO.File.WriteAllLines%2A> ve <xref:System.IO.File.WriteAllText%2A>gibi bir dosyaya metin yazmak ya da <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>ve <xref:System.IO.File.AppendText%2A>gibi bir dosyaya metin eklemek için statik yöntemler sağlar.  
  
- <xref:System.IO.Path>, dosya veya dizin yolu bilgilerine sahip dizeler içindir. <xref:System.IO.Path.Combine%2A> yöntemi ve .NET Core 2,1 ve üzeri sürümlerinde, dizelerin bitiştirilmesi için bir dosya veya dizin yolu oluşturma izni veren <xref:System.IO.Path.Join%2A> ve <xref:System.IO.Path.TryJoin%2A> yöntemleri içerir.

> [!NOTE]
> Aşağıdaki örneklerde yalnızca gereken minimum kod miktarı gösterilmektedir. Gerçek dünya uygulaması genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Örnek: StreamWriter ile eşzamanlı olarak metin yazma

Aşağıdaki örnek, bir kerede bir satırı yeni bir dosyaya zaman uyumlu olarak yazmak için <xref:System.IO.StreamWriter> sınıfını nasıl kullanacağınızı gösterir. <xref:System.IO.StreamWriter> nesne `using` bildiriminde bildirildiği ve örneklendiği için, <xref:System.IO.StreamWriter.Dispose%2A> yöntemi çağrılır, bu da akışı otomatik olarak boşaltır ve kapatır.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Örnek: bir StreamWriter ile eşzamanlı olarak metin ekleme

Aşağıdaki örnek, <xref:System.IO.StreamWriter> sınıfının, ilk örnekte oluşturulan metin dosyasına zaman uyumlu olarak metin ekleme için nasıl kullanılacağını gösterir.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Örnek: StreamWriter ile zaman uyumsuz olarak metin yazma

Aşağıdaki örnek, <xref:System.IO.StreamWriter> sınıfını kullanarak nasıl zaman uyumsuz olarak yeni bir dosyaya metin yazılacağını gösterir. <xref:System.IO.StreamWriter.WriteAsync%2A> yöntemini çağırmak için yöntem çağrısı bir `async` yöntemi içinde olmalıdır. C# Örnek, program C# giriş noktasındaki `async` değiştiricisi için destek ekleyen 7,1 veya sonraki bir sürümü gerektirir.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Örnek: dosya sınıfıyla metin yazın ve ekleyin

Aşağıdaki örnek, yeni bir dosyaya nasıl metin yazılacağını ve <xref:System.IO.File> sınıfını kullanarak aynı dosyaya yeni metin satırları ekleneceğini gösterir. <xref:System.IO.File.WriteAllText%2A> ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri açıp dosyayı otomatik olarak kapatır. <xref:System.IO.File.WriteAllText%2A> metoduna sağladığınız yol zaten varsa, dosyanın üzerine yazılır.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Nasıl yapılır: dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Nasıl yapılır: günlük dosyasını açma ve ekleme](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Nasıl yapılır: dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Dosya ve akış g/ç](../../../docs/standard/io/index.md)
