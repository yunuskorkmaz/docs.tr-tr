---
title: Zaman Uyumsuz Dosya G/Ç
description: .NET 'teki zaman uyumsuz dosya g/ç hakkında bilgi edinin. ReadAsync, WriteAsync ve daha fazlası gibi zaman uyumsuz işlemleri basitleştirecek zaman uyumsuz yöntemler hakkında bilgi edinin.
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
ms.openlocfilehash: 9506a366b6f1e363ec13550e5ed68c7176dd4d0a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598625"
---
# <a name="asynchronous-file-io"></a>Zaman Uyumsuz Dosya G/Ç

Zaman uyumsuz işlemler, yoğun kaynak kullanan I/O işlemlerini ana iş parçacığını engellemeden gerçekleştirmenizi sağlar. Bu performans açısından, zaman alan bir akış işleminin Kullanıcı arabirimi iş parçacığını engelleyebileceği ve uygulamanızın çalışmıyor gibi görünmesine neden olduğu bir Windows 8. x Mağazası uygulamasında veya masaüstü uygulamasında özellikle önemlidir.

4,5 .NET Framework başlayarak, g/ç türleri zaman uyumsuz işlemleri basitleştirecek zaman uyumsuz yöntemleri içerir. Bir zaman uyumsuz yöntem, adında `Async` içerir; örneğin <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> ve <xref:System.IO.TextReader.ReadToEndAsync%2A>. Bu zaman uyumsuz yöntemler, <xref:System.IO.Stream>, <xref:System.IO.FileStream> ve <xref:System.IO.MemoryStream> gibi akış sınıflarında ve <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter> gibi akışlarda okuma ve yazma işlemi yapan sınıflarda kullanılır.

.NET Framework 4 ve önceki sürümlerde, zaman uyumsuz G/Ç işlemlerini uygulamak için <xref:System.IO.Stream.BeginRead%2A> ve <xref:System.IO.Stream.EndRead%2A> gibi yöntemler kullanmanız gerekir. Bu yöntemler, eski kodu desteklemek için .NET Framework 4,5 ' de hala kullanılabilir; Ancak zaman uyumsuz yöntemler, zaman uyumsuz g/ç işlemlerini daha kolay uygulamanıza yardımcı olur.

C# ve Visual Basic, zaman uyumsuz programlama için iki anahtar sözcüğe sahiptir:

- Zaman uyumsuz bir işlem içeren bir yöntemi işaretlemek için kullanılan `Async` (Visual Basic) veya `async` (C#) değiştiricisi.

- Bir zaman uyumsuz yöntemin sonucuna uygulanan `Await` (Visual Basic) veya `await` (C#) işleci.

Zaman uyumsuz G/Ç işlemlerini uygulamak için, aşağıdaki örneklerde gösterildiği üzere zaman uyumsuz yöntemlerle bu anahtar sözcükleri kullanın. Daha fazla bilgi için bkz. [Async ve await (C#) ile](../../csharp/programming-guide/concepts/async/index.md) zaman uyumsuz programlama veya [Async ve await Ile zaman uyumsuz programlama (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).

Aşağıdaki örnek, dosyaları zaman uyumsuz olarak bir dizinden başka bir dizine kopyalamak için <xref:System.IO.FileStream> nesnelerini nasıl kullanacağınızı gösterir. <xref:System.Web.UI.WebControls.Button.Click> denetimi için <xref:System.Windows.Controls.Button> olay işleyicisinin, zaman uyumsuz bir yöntem çağırdığı için `async` değiştiricisi ile işaretlendiğine dikkat edin.

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

Sonraki örnek öncekine benzer, ancak bir metin dosyasının içeriğini zaman uyumsuz olarak okumak için <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> nesnelerini kullanır.

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

Sonraki örnekte, bir dosyayı bir Windows 8. x Mağazası uygulamasında bir dosya olarak açmak için kullanılan arka plan kod dosyası ve XAML dosyası ve <xref:System.IO.Stream> sınıfının bir örneğini kullanarak içeriğini okumak gösterilmektedir <xref:System.IO.StreamReader> . Dosyayı bir akış olarak açmak ve içeriğini okumak için zaman uyumsuz yöntemler kullanır.

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.Stream>
- [Dosya ve akış g/ç](index.md)
- [Async ve await ile zaman uyumsuz programlama (C#)](../../csharp/programming-guide/concepts/async/index.md)
- [Async ve await ile zaman uyumsuz programlama (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
