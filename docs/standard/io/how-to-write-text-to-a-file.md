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
ms.openlocfilehash: 70b2d04f381fdbc1ae47b1c90649df045e111afa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779412"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="89194-102">Nasıl yapılır: Bir Dosyaya Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="89194-102">How to: Write Text to a File</span></span>
<span data-ttu-id="89194-103">.NET Framework uygulamaları için bir dosyaya metin yazabilirsiniz bu konuda gösterildiği farklı bir şekilde veya [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="89194-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="89194-104">Aşağıdaki sınıflar ve yöntemler genellikle bir dosyaya metin yazmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="89194-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="89194-105"><xref:System.IO.StreamWriter> -bir dosyasına eşzamanlı yazma yöntemleri içeren (<xref:System.IO.StreamWriter.Write%2A> veya <xref:System.IO.TextWriter.WriteLine%2A>) veya zaman uyumsuz olarak (<xref:System.IO.StreamWriter.WriteAsync%2A> ve <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="89194-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="89194-106"><xref:System.IO.File> – .NET Framework uygulamaları ile kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="89194-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="89194-107">Metin gibi bir dosyaya yazmak için statik yöntemler sağlar <xref:System.IO.File.WriteAllLines%2A> ve <xref:System.IO.File.WriteAllText%2A>, veya bir dosyaya metin eklemek için (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> veya <xref:System.IO.File.AppendText%2A>).</span><span class="sxs-lookup"><span data-stu-id="89194-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="89194-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - ile kullanılmak üzere [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="89194-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="89194-109">Metni bir dosyaya yazmak için zaman uyumsuz yöntemleri içerir ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) veya [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) veya bir dosyaya metin eklemek için ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) veya [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span><span class="sxs-lookup"><span data-stu-id="89194-109">It contains asynchronous methods to write text to a file ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) or [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) or to append text to a file ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) or [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span></span>  

- <span data-ttu-id="89194-110"><xref:System.IO.Path> -Dosya veya dizin yolu bilgilerini içeren dizeleri kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="89194-110"><xref:System.IO.Path> - to be used on strings that contain file or directory path information.</span></span> <span data-ttu-id="89194-111">İçerdiği <xref:System.IO.Path.Combine%2A> yöntemi bir dosya veya dizin yolu oluşturmak için dizelerin bir birleşimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="89194-111">It contains the <xref:System.IO.Path.Combine%2A> method, which allows concatenation of strings to build a file or directory path.</span></span>


 <span data-ttu-id="89194-112">Örnekler, gerçekleştirilen görevdeki odaklanmak için basit tutulmuştur.</span><span class="sxs-lookup"><span data-stu-id="89194-112">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="89194-113">Bu nedenle, varsa minimum hata denetimi ve özel durum işleme örnekleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="89194-113">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="89194-114">Bir gerçek yaşam uygulaması genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="89194-114">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89194-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="89194-115">Example</span></span>  
 <span data-ttu-id="89194-116">Aşağıdaki örnek, zaman uyumlu olarak yeni kullanarak bir dosyaya metin yazma işlemi gösterilmektedir <xref:System.IO.StreamWriter> sınıfı, her defasında bir satır.</span><span class="sxs-lookup"><span data-stu-id="89194-116">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="89194-117">Yeni metin dosyası, kullanıcının Belgelerim klasörüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="89194-117">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="89194-118">Çünkü <xref:System.IO.StreamWriter> nesne bildirildi ve içinde örneklenen bir `using` deyimi <xref:System.IO.StreamWriter.Dispose%2A> metodunu çağırmak otomatik olarak boşaltır ve akışı kapatır.</span><span class="sxs-lookup"><span data-stu-id="89194-118">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="89194-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="89194-119">Example</span></span>  
 <span data-ttu-id="89194-120">Aşağıdaki örnek, var olan bir kullanarak dosyaya metin ekleme işlemi gösterilmektedir <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="89194-120">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="89194-121">Önceki örnekte aynı metin dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="89194-121">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="89194-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="89194-122">Example</span></span>  
 <span data-ttu-id="89194-123">Aşağıdaki örnek, zaman uyumsuz olarak yeni kullanarak bir dosyaya metin yazma işlemi gösterilmektedir <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="89194-123">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="89194-124">Çağırmak için <xref:System.IO.StreamWriter.WriteAsync%2A> yöntem, yöntem çağrısının içinde olması gerekir bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="89194-124">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="89194-125">Yeni metin dosyası, kullanıcının Belgelerim klasörüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="89194-125">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="89194-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="89194-126">Example</span></span>  
 <span data-ttu-id="89194-127">Aşağıdaki örnek, yeni bir dosyaya metin yazma ve kullanarak aynı dosya için yeni satırlık metin ekleme işlemi gösterilmektedir <xref:System.IO.File> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="89194-127">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="89194-128"><xref:System.IO.File.WriteAllText%2A> Ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri açın ve dosyayı otomatik olarak kapatın.</span><span class="sxs-lookup"><span data-stu-id="89194-128">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="89194-129">Sağladığınız yolun, <xref:System.IO.File.WriteAllText%2A> yöntemi zaten var, dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="89194-129">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="89194-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="89194-130">Example</span></span>  
 <span data-ttu-id="89194-131">Aşağıdaki örnek, zaman uyumsuz olarak kullanıcı girişi için bir metin dosyasına yazma işlemi gösterilmektedir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="89194-131">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="89194-132">Güvenlik konuları nedeniyle bir dosya açma bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama genellikle kullanımını gerektirir bir [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) denetimi.</span><span class="sxs-lookup"><span data-stu-id="89194-132">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) control.</span></span> <span data-ttu-id="89194-133">Bu örnekte, `FileOpenPicker` metin dosyaları gösterecek şekilde filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="89194-133">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89194-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89194-134">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.Path>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="89194-135">Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="89194-135">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="89194-136">Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="89194-136">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="89194-137">Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme</span><span class="sxs-lookup"><span data-stu-id="89194-137">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="89194-138">Nasıl yapılır: Dosyadan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="89194-138">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="89194-139">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="89194-139">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
