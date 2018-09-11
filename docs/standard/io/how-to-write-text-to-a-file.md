---
title: 'Nasıl yapılır: Bir Dosyaya Metin Yazma'
ms.date: 03/30/2017
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
ms.openlocfilehash: bc8082175047271c92f9a9a17a49534ffc9546a9
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365867"
---
# <a name="how-to-write-text-to-a-file"></a>Nasıl yapılır: Bir Dosyaya Metin Yazma
.NET Framework uygulamaları için bir dosyaya metin yazabilirsiniz bu konuda gösterildiği farklı bir şekilde veya [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar. Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:  
  
-   <xref:System.IO.StreamWriter> -bir dosyasına eşzamanlı yazma yöntemleri içeren (<xref:System.IO.StreamWriter.Write%2A> veya <xref:System.IO.TextWriter.WriteLine%2A>) veya zaman uyumsuz olarak (<xref:System.IO.StreamWriter.WriteAsync%2A> ve <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
-   <xref:System.IO.File> – .NET Framework uygulamaları ile kullanılacak. Metin gibi bir dosyaya yazmak için statik yöntemler sağlar <xref:System.IO.File.WriteAllLines%2A> ve <xref:System.IO.File.WriteAllText%2A>, veya bir dosyaya metin eklemek için (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> veya <xref:System.IO.File.AppendText%2A>).  
  
-   [FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - ile kullanılmak üzere [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar. Metni bir dosyaya yazmak için zaman uyumsuz yöntemleri içerir ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) veya [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) veya bir dosyaya metin eklemek için ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) veya [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).  

- <xref:System.IO.Path> -Dosya veya dizin yolu bilgilerini içeren dizeleri kullanılacak. İçerdiği <xref:System.IO.Path.Combine%2A> yöntemi bir dosya veya dizin yolu oluşturmak için dizelerin bir birleşimini sağlar.


 Örnekler, gerçekleştirilen görevdeki odaklanmak için basit tutulmuştur. Bu nedenle, varsa minimum hata denetimi ve özel durum işleme örnekleri gerçekleştirin. Bir gerçek yaşam uygulaması genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, zaman uyumlu olarak yeni kullanarak bir dosyaya metin yazma işlemi gösterilmektedir <xref:System.IO.StreamWriter> sınıfı, her defasında bir satır. Yeni metin dosyası, kullanıcının Belgelerim klasörüne kaydedilir. Çünkü <xref:System.IO.StreamWriter> nesne bildirildi ve içinde örneklenen bir `using` deyimi <xref:System.IO.StreamWriter.Dispose%2A> metodunu çağırmak otomatik olarak boşaltır ve akışı kapatır.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, var olan bir kullanarak dosyaya metin ekleme işlemi gösterilmektedir <xref:System.IO.StreamWriter> sınıfı. Önceki örnekte aynı metin dosyası kullanır.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, zaman uyumsuz olarak yeni kullanarak bir dosyaya metin yazma işlemi gösterilmektedir <xref:System.IO.StreamWriter> sınıfı. Çağırmak için <xref:System.IO.StreamWriter.WriteAsync%2A> yöntem, yöntem çağrısının içinde olması gerekir bir `async` yöntemi. Yeni metin dosyası, kullanıcının Belgelerim klasörüne kaydedilir.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yeni bir dosyaya metin yazma ve kullanarak aynı dosya için yeni satırlık metin ekleme işlemi gösterilmektedir <xref:System.IO.File> sınıfı. <xref:System.IO.File.WriteAllText%2A> Ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri açın ve dosyayı otomatik olarak kapatın. Sağladığınız yolun, <xref:System.IO.File.WriteAllText%2A> yöntemi zaten var, dosyanın üzerine yazılır.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, zaman uyumsuz olarak kullanıcı girişi için bir metin dosyasına yazma işlemi gösterilmektedir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama. Güvenlik konuları nedeniyle bir dosya açma bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama genellikle kullanımını gerektirir bir [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) denetimi. Bu örnekte, `FileOpenPicker` metin dosyaları gösterecek şekilde filtrelenir.  
  
```xaml  
<Page  
    x:Class="OpenFileWindowsStore.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:OpenFileWindowsStore"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Button Content="save text to a file" HorizontalAlignment="Left" Margin="103,417,0,0" VerticalAlignment="Top"   
                Width="329" Height="86" FontSize="35" Click="Button_Click"/>  
        <TextBox Name="UserInputTextBox"  FontSize="18" HorizontalAlignment="Left" Margin="106,146,0,0"   
                 TextWrapping="Wrap" Text="Write some text here, and select a file to write it to." VerticalAlignment="Top"   
                 Height="201" Width="558" AcceptsReturn="True"/>  
        <TextBlock Name="StatusTextBox" HorizontalAlignment="Left" Margin="106,570,0,147" TextWrapping="Wrap" Text="Status:"   
                   VerticalAlignment="Center" Height="51" Width="1074" FontSize="18" />  
    </Grid>  
</Page>  
```  
  
 [!code-csharp[OpenFileWindowsStore#Code](../../../samples/snippets/csharp/VS_Snippets_CLR/openfilewindowsstore/cs/mainpage.xaml.cs#code)]
 [!code-vb[OpenFileWindowsStore#Code](../../../samples/snippets/visualbasic/VS_Snippets_CLR/openfilewindowsstore/vb/mainpage.xaml.vb#code)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.Path>  
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
- [Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: Dosyadan Metin Okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
