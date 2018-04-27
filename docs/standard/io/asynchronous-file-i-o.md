---
title: Zaman uyumsuz dosya t-O
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 23
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e0c67c9b397dfcd6f6ba947c2876919693c4f472
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="asynchronous-file-io"></a>Zaman Uyumsuz Dosya G/Ç
Zaman uyumsuz işlemler, yoğun kaynak kullanan I/O işlemlerini ana iş parçacığını engellemeden gerçekleştirmenizi sağlar. Bu performans artışı özellikle bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] veya [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)] uygulamasında önemlidir, çünkü UI iş parçacığını engelleyen zaman alan bir işlem uygulamanızın çalışmıyor gibi gözükmesine sebep olabilir.  
  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ile başlayarak G/Ç türleri, zaman uyumsuz işlemleri basitleştirmek için zaman uyumsuz yöntemleri içerir. Bir zaman uyumsuz yöntem, adında `Async` içerir; örneğin <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> ve <xref:System.IO.TextReader.ReadToEndAsync%2A>. Bu zaman uyumsuz yöntemler, <xref:System.IO.Stream>, <xref:System.IO.FileStream> ve <xref:System.IO.MemoryStream> gibi akış sınıflarında ve <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter> gibi akışlarda okuma ve yazma işlemi yapan sınıflarda kullanılır.  
  
 .NET Framework 4 ve önceki sürümlerde, zaman uyumsuz G/Ç işlemlerini uygulamak için <xref:System.IO.Stream.BeginRead%2A> ve <xref:System.IO.Stream.EndRead%2A> gibi yöntemler kullanmanız gerekir. Bu yöntemler eski kodu desteklemek için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] içinde hala kullanılabilirdir; ancak zaman uyumsuz yöntemler, zaman uyumsuz G/Ç işlemlerini daha kolay uygulamanıza yardımcı olur.  
  
 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] ile başlayarak, Visual Studio zaman uyumsuz programlama için iki anahtar sözcük sağlar:  
  
 Zaman uyumsuz bir işlem içeren bir yöntemi işaretlemek için kullanılan `Async` (Visual Basic) veya `async` (C#) değiştiricisi.  
  
 Bir zaman uyumsuz yöntemin sonucuna uygulanan `Await` (Visual Basic) veya `await` (C#) işleci.  
  
 Zaman uyumsuz G/Ç işlemlerini uygulamak için, aşağıdaki örneklerde gösterildiği üzere zaman uyumsuz yöntemlerle bu anahtar sözcükleri kullanın. Daha fazla bilgi için bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7).  
  
 Aşağıdaki örnek, dosyaları zaman uyumsuz olarak bir dizinden başka bir dizine kopyalamak için <xref:System.IO.FileStream> nesnelerini nasıl kullanacağınızı gösterir. <xref:System.Web.UI.WebControls.Button.Click> denetimi için <xref:System.Windows.Controls.Button> olay işleyicisinin, zaman uyumsuz bir yöntem çağırdığı için `async` değiştiricisi ile işaretlendiğine dikkat edin.  
  
 [!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
 [!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]  
  
 Sonraki örnek öncekine benzer, ancak bir metin dosyasının içeriğini zaman uyumsuz olarak okumak için <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> nesnelerini kullanır.  
  
 [!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
 [!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]  
  
 Sonraki örnek, bir <xref:System.IO.Stream> uygulamasında dosyayı [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] olarak açmak ve <xref:System.IO.StreamReader> sınıfının bir örneğiyle içeriğini okumak için kullanılan arka plan kod dosyasını ve XAML dosyasını gösterir. Dosyayı bir akış olarak açmak ve içeriğini okumak için zaman uyumsuz yöntemler kullanır.  
  
 [!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
 [!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]  
  
 [!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IO.Stream>  
 [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)  
 [Async ve Await ile Zaman Uyumsuz Programlama](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)
