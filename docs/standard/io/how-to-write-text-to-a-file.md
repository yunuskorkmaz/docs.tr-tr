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
ms.openlocfilehash: 13fa71487f143b1054cd2014fa74a1c7245ab31b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577131"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="16e1e-102">Nasıl yapılır: Bir Dosyaya Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="16e1e-102">How to: Write Text to a File</span></span>
<span data-ttu-id="16e1e-103">.NET Framework uygulamaları için bir dosyaya metin yazabilirler bu konuda gösterir farklı bir şekilde veya [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="16e1e-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="16e1e-104">Genellikle aşağıdaki sınıflar ve yöntemler metin bir dosyaya yazmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="16e1e-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="16e1e-105"><xref:System.IO.StreamWriter> -zaman uyumlu bir dosyaya yazmak için yöntemler içerir (<xref:System.IO.StreamWriter.Write%2A> veya <xref:System.IO.TextWriter.WriteLine%2A>) veya zaman uyumsuz olarak (<xref:System.IO.StreamWriter.WriteAsync%2A> ve <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="16e1e-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="16e1e-106"><xref:System.IO.File> – .NET Framework uygulamaları ile kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="16e1e-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="16e1e-107">Metin gibi bir dosyaya yazmak için statik yöntemler sağlar <xref:System.IO.File.WriteAllLines%2A> ve <xref:System.IO.File.WriteAllText%2A>, veya metin dosyasına Ekle (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> veya <xref:System.IO.File.AppendText%2A>).</span><span class="sxs-lookup"><span data-stu-id="16e1e-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="16e1e-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - ile kullanılmak üzere [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="16e1e-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="16e1e-109">Metin bir dosyaya yazmak için zaman uyumsuz yöntemleri içeren ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) veya [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) veya metin dosyasına Ekle ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) veya [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span><span class="sxs-lookup"><span data-stu-id="16e1e-109">It contains asynchronous methods to write text to a file ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) or [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) or to append text to a file ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) or [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span></span>  

- <span data-ttu-id="16e1e-110"><xref:System.IO.Path> -Dosya veya dizin yolunu bilgilerini içeren dizeleri kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="16e1e-110"><xref:System.IO.Path> - to be used on strings that contain file or directory path information.</span></span> <span data-ttu-id="16e1e-111">İçerdiği <xref:System.IO.Path.Combine%2A> bir dosya veya dizin yolu oluşturmak için dizeleri birleşimini sağlar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="16e1e-111">It contains the <xref:System.IO.Path.Combine%2A> method, which allows concatenation of strings to build a file or directory path.</span></span>


 <span data-ttu-id="16e1e-112">Örnekler gerçekleştirilen görevde odaklanmak için basit tutulmuştur.</span><span class="sxs-lookup"><span data-stu-id="16e1e-112">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="16e1e-113">Varsa, en az hata denetimi ve özel durum işleme örnekleri bu nedenle, gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="16e1e-113">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="16e1e-114">Gerçek dünya uygulama genellikle daha sağlam hata denetimi ve özel durum işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="16e1e-114">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16e1e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e1e-115">Example</span></span>  
 <span data-ttu-id="16e1e-116">Aşağıdaki örnekte, zaman uyumlu olarak kullanarak yeni bir dosya için metin yazmak gösterilmiştir <xref:System.IO.StreamWriter> sınıfı, bir defada bir satır.</span><span class="sxs-lookup"><span data-stu-id="16e1e-116">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="16e1e-117">Yeni metin dosyası kullanıcının Belgelerim klasörüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="16e1e-117">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="16e1e-118">Çünkü <xref:System.IO.StreamWriter> nesne bildirilir ve içinde örneği bir `using` deyimi, <xref:System.IO.StreamWriter.Dispose%2A> yöntemi çağrılır, otomatik olarak boşaltır ve akış kapatır.</span><span class="sxs-lookup"><span data-stu-id="16e1e-118">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="16e1e-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e1e-119">Example</span></span>  
 <span data-ttu-id="16e1e-120">Aşağıdaki örnekte, metin dosyası kullanılarak, mevcut bir için eklenecek gösterilmiştir <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="16e1e-120">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="16e1e-121">Önceki örnekte aynı metin dosyasından kullanır.</span><span class="sxs-lookup"><span data-stu-id="16e1e-121">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="16e1e-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e1e-122">Example</span></span>  
 <span data-ttu-id="16e1e-123">Aşağıdaki örnekte, metin kullanarak yeni bir dosya için zaman uyumsuz olarak yazmak gösterilmiştir <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="16e1e-123">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="16e1e-124">Çağırmak için <xref:System.IO.StreamWriter.WriteAsync%2A> yöntemi, yöntem çağrısı içinde olması gerekir bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="16e1e-124">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="16e1e-125">Yeni metin dosyası kullanıcının Belgelerim klasörüne kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="16e1e-125">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="16e1e-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e1e-126">Example</span></span>  
 <span data-ttu-id="16e1e-127">Aşağıdaki örnek yeni bir dosyaya metin yazma ve kullanarak aynı dosya için yeni satırlık metin eklenecek gösterilmiştir <xref:System.IO.File> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="16e1e-127">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="16e1e-128"><xref:System.IO.File.WriteAllText%2A> Ve <xref:System.IO.File.AppendAllLines%2A> yöntemleri açın ve dosyanın otomatik olarak kapanır.</span><span class="sxs-lookup"><span data-stu-id="16e1e-128">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="16e1e-129">Sağladığınız yolun varsa <xref:System.IO.File.WriteAllText%2A> yöntemi zaten var, dosyanın üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="16e1e-129">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="16e1e-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e1e-130">Example</span></span>  
 <span data-ttu-id="16e1e-131">Aşağıdaki örnek, bir metin dosyasına kullanıcı girişini zaman uyumsuz olarak yazmak gösterilmiştir bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="16e1e-131">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="16e1e-132">Güvenlik nedeniyle, bir dosyanın açılması bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama genellikle kullanılmasını gerektiren bir [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) denetim.</span><span class="sxs-lookup"><span data-stu-id="16e1e-132">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) control.</span></span> <span data-ttu-id="16e1e-133">Bu örnekte, `FileOpenPicker` metin dosyaları göstermek için filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="16e1e-133">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16e1e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16e1e-134">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.Path>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="16e1e-135">Nasıl yapılır: Dizinleri ve Dosyaları Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="16e1e-135">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="16e1e-136">Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma</span><span class="sxs-lookup"><span data-stu-id="16e1e-136">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="16e1e-137">Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme</span><span class="sxs-lookup"><span data-stu-id="16e1e-137">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="16e1e-138">Nasıl yapılır: Dosyadan Metin Okuma</span><span class="sxs-lookup"><span data-stu-id="16e1e-138">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="16e1e-139">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="16e1e-139">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
