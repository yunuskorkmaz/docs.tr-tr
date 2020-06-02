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
ms.openlocfilehash: 395344accf5be416fbcc527e51ba83408f9c5810
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291740"
---
# <a name="how-to-write-text-to-a-file"></a>Nasıl yapılır: bir dosyaya metin yazma
Bu konu başlığı altında, bir .NET uygulaması için bir dosyaya metin yazmanın farklı yolları gösterilmektedir.

Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:  
  
- <xref:System.IO.StreamWriter>bir dosyaya zaman uyumlu ( <xref:System.IO.StreamWriter.Write%2A> ve <xref:System.IO.TextWriter.WriteLine%2A> ) veya zaman uyumsuz ( <xref:System.IO.StreamWriter.WriteAsync%2A> ve) yazma yöntemleri içerir <xref:System.IO.StreamWriter.WriteLineAsync%2A> .  
  
- <xref:System.IO.File>, ve gibi bir dosyaya metin yazmak için statik yöntemler sağlar; örneğin, <xref:System.IO.File.WriteAllLines%2A> <xref:System.IO.File.WriteAllText%2A> ve gibi bir dosyaya metin ekler <xref:System.IO.File.AppendAllLines%2A> <xref:System.IO.File.AppendAllText%2A> <xref:System.IO.File.AppendText%2A> .  
  
- <xref:System.IO.Path>dosya veya dizin yolu bilgilerine sahip dizeler içindir. Bu yöntem, ve <xref:System.IO.Path.Combine%2A> .NET Core 2,1 ve sonraki sürümlerinde, <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> dizelerin bir dosya ya da dizin yolu oluşturmak için bitiştirilmesi sağlayan ve yöntemleri içerir.

> [!NOTE]
> Aşağıdaki örneklerde yalnızca gereken minimum kod miktarı gösterilmektedir. Gerçek dünya uygulaması genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Örnek: StreamWriter ile eşzamanlı olarak metin yazma

Aşağıdaki örnek, <xref:System.IO.StreamWriter> bir kerede bir satırı yeni bir dosyaya zaman uyumlu olarak yazmak için sınıfını nasıl kullanacağınızı gösterir. <xref:System.IO.StreamWriter>Nesne bir ifadede bildirildiği ve örneklendiği `using` için <xref:System.IO.StreamWriter.Dispose%2A> yöntem çağrılır, bu da akışı otomatik olarak boşaltır ve kapatır.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Örnek: bir StreamWriter ile eşzamanlı olarak metin ekleme

Aşağıdaki örnek, <xref:System.IO.StreamWriter> sınıfının, ilk örnekte oluşturulan metin dosyasına zaman uyumlu olarak metin ekleme için nasıl kullanılacağını gösterir.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Örnek: StreamWriter ile zaman uyumsuz olarak metin yazma

Aşağıdaki örnek, sınıfını kullanarak nasıl zaman uyumsuz olarak yeni bir dosyaya metin yazılacağını gösterir <xref:System.IO.StreamWriter> . Yöntemi çağırmak için <xref:System.IO.StreamWriter.WriteAsync%2A> Yöntem çağrısı bir yöntem içinde olmalıdır `async` . C# örneği, `async` program giriş noktasındaki değiştirici için destek ekleyen c# 7,1 veya üstünü gerektirir.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Örnek: dosya sınıfıyla metin yazın ve ekleyin

Aşağıdaki örnek, yeni bir dosyaya nasıl metin yazılacağını ve sınıfı kullanılarak aynı dosyaya yeni metin satırları ekleneceğini gösterir <xref:System.IO.File> . <xref:System.IO.File.WriteAllText%2A>Ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri, dosyayı otomatik olarak açar ve kapatır. Metoda sağladığınız yol <xref:System.IO.File.WriteAllText%2A> zaten varsa, dosyanın üzerine yazılır.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Nasıl yapılır: dizinleri ve dosyaları numaralandırma](how-to-enumerate-directories-and-files.md)
- [Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma](how-to-read-and-write-to-a-newly-created-data-file.md)
- [Nasıl yapılır: günlük dosyasını açma ve ekleme](how-to-open-and-append-to-a-log-file.md)
- [Nasıl yapılır: dosyadan metin okuma](how-to-read-text-from-a-file.md)
- [Dosya ve akış G/Ç](index.md)
