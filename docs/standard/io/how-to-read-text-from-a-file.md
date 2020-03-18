---
title: 'Nasıl yapilir: Dosyadaki metni okuma'
ms.date: 01/03/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155730"
---
# <a name="how-to-read-text-from-a-file"></a>Nasıl yapilir: Dosyadaki metni okuma
Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir. Her iki örnekte de, <xref:System.IO.StreamReader> sınıfın örneğini oluşturduğunuzda, dosyaya göreli veya mutlak yolu sağlarsınız.
  
> [!NOTE]
> Windows Runtime dosyaları okumak ve yazmak için farklı akış türleri sağladığından, bu kod örnekleri Evrensel Windows (UWP) uygulamaları için geliştirme için geçerli değildir. UWP uygulamasındaki bir dosyadaki metnin nasıl okunduğunu gösteren bir örnek [için, Bkz. Quickstart: Okuma ve yazma dosyaları.](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)) .NET Framework akışları ile Windows Runtime akışları arasında nasıl dönüşüm yapılacağını gösteren örnekler için [bkz.](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Örnek: Konsol uygulamasında eşzamanlı okuma  
Aşağıdaki örnekte, konsol uygulaması içinde eşzamanlı okuma işlemi gösterilmektedir. Bu örnek, akış okuyucukullanarak metin dosyasını açar, içeriği bir dizeye kopyalar ve dizeyi konsola çıkar.  
  
> [!IMPORTANT]
> Örnek, *TestFile.txt* adlı bir dosyanın uygulamayla aynı klasörde zaten mevcut olduğunu varsayar.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Örnek: Bir WPF uygulamasında asynchronous okunur
 Aşağıdaki örnek, bir Windows Sunu Vakfı (WPF) uygulamasında eşzamanlı okuma işlemini gösterir.  
  
> [!IMPORTANT]
> Örnek, *TestFile.txt* adlı bir dosyanın uygulamayla aynı klasörde zaten mevcut olduğunu varsayar.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Asynchronous dosya I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Nasıl yapılsın: Dizin listesi oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Quickstart: Dosyaları okuma ve yazma](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Nasıl?](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılı: Günlük dosyasını açma ve ekle](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yazılır: Dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Nasıl yapilir: Bir dizedeki karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Nasıl yazılır: Karakterleri bir dize yazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Dosya ve akış G/Ç](../../../docs/standard/io/index.md)
