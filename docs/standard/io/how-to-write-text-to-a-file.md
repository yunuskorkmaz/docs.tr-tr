---
title: 'Nasıl yazılır: Dosyaya metin yazma'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160254"
---
# <a name="how-to-write-text-to-a-file"></a>Nasıl yazılır: Dosyaya metin yazma
Bu konu, bir .NET uygulaması için bir dosyaya metin yazmanın farklı yollarını gösterir.

Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:  
  
- <xref:System.IO.StreamWriter>bir dosyaya eşzamanlı olarak<xref:System.IO.StreamWriter.Write%2A> (ve) <xref:System.IO.TextWriter.WriteLine%2A>veya eşzamanlı olarak<xref:System.IO.StreamWriter.WriteAsync%2A> (ve) <xref:System.IO.StreamWriter.WriteLineAsync%2A>yazma yöntemleri içerir.  
  
- <xref:System.IO.File>gibi bir dosyaya metin yazmak <xref:System.IO.File.WriteAllLines%2A> için <xref:System.IO.File.WriteAllText%2A>statik yöntemler sağlar ve , veya <xref:System.IO.File.AppendAllLines%2A>bir <xref:System.IO.File.AppendAllText%2A>dosyaya metin eklemek için , , ve <xref:System.IO.File.AppendText%2A>.  
  
- <xref:System.IO.Path>dosya veya dizin yolu bilgilerine sahip dizeleri içindir. Bir dosya <xref:System.IO.Path.Combine%2A> veya dizin yolu oluşturmak için dizeleri <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> biraraya getiren yöntem ve .NET Core 2.1 ve daha sonra, ve daha sonra, ve yöntemleri içerir.

> [!NOTE]
> Aşağıdaki örnekler, yalnızca gereken minimum kod miktarını gösterir. Gerçek bir uygulama genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Örnek: StreamWriter ile eşzamanlı metin yazma

Aşağıdaki örnek, bir seferde <xref:System.IO.StreamWriter> yeni bir dosyaya eşit olarak metin yazmak için sınıfın nasıl kullanılacağını gösterir. <xref:System.IO.StreamWriter> Nesne bir `using` deyimde beyan edilip anında çağrıldığı için, <xref:System.IO.StreamWriter.Dispose%2A> yöntem çağrılır ve bu yöntem akışı otomatik olarak temizler ve kapatır.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Örnek: StreamWriter ile eşzamanlı olarak metin ekle

Aşağıdaki örnekte, ilk <xref:System.IO.StreamWriter> örnekte oluşturulan metin dosyasına eşit olarak metin eklemek için sınıfın nasıl kullanılacağı gösterilmektedir.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Örnek: StreamWriter ile eşzamanlı metin yazmak

Aşağıdaki örnek, sınıfı kullanarak yeni bir dosyaya eş <xref:System.IO.StreamWriter> senkronize metin yazmanın nasıl yapılacağını gösterir. <xref:System.IO.StreamWriter.WriteAsync%2A> Yöntemi çağırmak için yöntem çağrısının bir `async` yöntem içinde olması gerekir. C# örneği C# 7.1 veya daha sonra `async` gerektirir, bu da program giriş noktasındaki değiştirici için destek ekler.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Örnek: Dosya sınıfıyla metin yazma ve ekle

Aşağıdaki örnek, yeni bir dosyaya metin yazmanın ve sınıfı kullanarak aynı <xref:System.IO.File> dosyaya yeni metin satırlarının nasıl eklenilen olduğunu gösterir. Ve <xref:System.IO.File.WriteAllText%2A> <xref:System.IO.File.AppendAllLines%2A> yöntemleri dosyayı otomatik olarak açıp kapatır. <xref:System.IO.File.WriteAllText%2A> Yönteme sağladığınız yol zaten varsa, dosya üzerine yazılır.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Dizinleri ve dosyaları sayısal](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Nasıl yapılı: Günlük dosyasını açma ve ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Nasıl yapilir: Dosyadaki metni okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)
