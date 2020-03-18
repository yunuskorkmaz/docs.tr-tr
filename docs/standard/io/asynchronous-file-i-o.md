---
title: Zaman Uyumsuz Dosya G/Ç
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
ms.openlocfilehash: 66e7d01f37a1119b9d2076a9131aa40f26d15625
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708197"
---
# <a name="asynchronous-file-io"></a>Zaman Uyumsuz Dosya G/Ç

Zaman uyumsuz işlemler, yoğun kaynak kullanan I/O işlemlerini ana iş parçacığını engellemeden gerçekleştirmenizi sağlar. Bu performans değerlendirmesi, zaman alan bir akış işleminin UI iş parçacığının engellenebileceği ve uygulamanızın çalışmıyormuş gibi görünmesini sağlayabildiği bir Windows 8.x Store uygulaması veya masaüstü uygulamasında özellikle önemlidir.

.NET Framework 4.5 ile başlayarak, G/Ç türleri eşzamanlı işlemleri basitleştirmek için async yöntemleri içerir. Bir zaman uyumsuz yöntem, adında `Async` içerir; örneğin <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> ve <xref:System.IO.TextReader.ReadToEndAsync%2A>. Bu zaman uyumsuz yöntemler, <xref:System.IO.Stream>, <xref:System.IO.FileStream> ve <xref:System.IO.MemoryStream> gibi akış sınıflarında ve <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter> gibi akışlarda okuma ve yazma işlemi yapan sınıflarda kullanılır.

.NET Framework 4 ve önceki sürümlerde, zaman uyumsuz G/Ç işlemlerini uygulamak için <xref:System.IO.Stream.BeginRead%2A> ve <xref:System.IO.Stream.EndRead%2A> gibi yöntemler kullanmanız gerekir. Bu yöntemler eski kodu desteklemek için .NET Framework 4.5'te hala kullanılabilir; ancak, async yöntemleri asynchronous G/Ç işlemlerini daha kolay uygulamanıza yardımcı olur.

C# ve Visual Basic'in her birinin asynchronous programlama için iki anahtar öğesi vardır:

- Zaman uyumsuz bir işlem içeren bir yöntemi işaretlemek için kullanılan `Async` (Visual Basic) veya `async` (C#) değiştiricisi.

- Bir zaman uyumsuz yöntemin sonucuna uygulanan `Await` (Visual Basic) veya `await` (C#) işleci.

Zaman uyumsuz G/Ç işlemlerini uygulamak için, aşağıdaki örneklerde gösterildiği üzere zaman uyumsuz yöntemlerle bu anahtar sözcükleri kullanın. Daha fazla bilgi için, [async ile Asynchronous programlama bakın ve (C#)](../../csharp/programming-guide/concepts/async/index.md) veya [Async ve Await (Visual Basic) ile Asynchronous Programlama](../../visual-basic/programming-guide/concepts/async/index.md)bekliyor.

Aşağıdaki örnek, dosyaları zaman uyumsuz olarak bir dizinden başka bir dizine kopyalamak için <xref:System.IO.FileStream> nesnelerini nasıl kullanacağınızı gösterir. <xref:System.Web.UI.WebControls.Button.Click> denetimi için <xref:System.Windows.Controls.Button> olay işleyicisinin, zaman uyumsuz bir yöntem çağırdığı için `async` değiştiricisi ile işaretlendiğine dikkat edin.

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

Sonraki örnek öncekine benzer, ancak bir metin dosyasının içeriğini zaman uyumsuz olarak okumak için <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> nesnelerini kullanır.

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

Sonraki örnek, bir Windows 8.x Store uygulamasında bir dosyayı <xref:System.IO.Stream> açmak ve sınıfın bir örneğini kullanarak içeriğini okumak için kullanılan <xref:System.IO.StreamReader> kod arkası dosyasını ve XAML dosyasını gösterir. Dosyayı bir akış olarak açmak ve içeriğini okumak için zaman uyumsuz yöntemler kullanır.

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Stream>
- [Dosya ve Akış G/Ç'si](index.md)
- [Async ve await ile asynchronous programlama (C#)](../../csharp/programming-guide/concepts/async/index.md)
- [Async ve Await ile Asynchronous Programlama (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
