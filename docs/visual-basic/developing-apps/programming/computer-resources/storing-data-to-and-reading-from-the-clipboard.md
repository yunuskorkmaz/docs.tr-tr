---
title: Verileri Panoda depolama ve (Visual Basic) panodan okuma
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7bb4ad56f0a039aa7b23d7f0612aaab9366cb9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="cc09a-102">Verileri Panoda depolama ve (Visual Basic) panodan okuma</span><span class="sxs-lookup"><span data-stu-id="cc09a-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="cc09a-103">Pano, metin ve resimler gibi verileri depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc09a-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="cc09a-104">Pano tüm etkin işlemler tarafından paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc09a-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="cc09a-105">`My.Computer.Clipboard` Nesne kolayca panoya erişmek için okuma ve yazma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc09a-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="cc09a-106">Panodan okuma</span><span class="sxs-lookup"><span data-stu-id="cc09a-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="cc09a-107">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> yöntemi Panodaki metni okuyun.</span><span class="sxs-lookup"><span data-stu-id="cc09a-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="cc09a-108">Aşağıdaki kod metni okur ve bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cc09a-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="cc09a-109">Örneğin düzgün çalışması Panodaki depolanan metni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc09a-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 <span data-ttu-id="cc09a-110">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc09a-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="cc09a-111">Kod parçacığı Seçici bulunur **Windows Forms uygulamaları > Pano**.</span><span class="sxs-lookup"><span data-stu-id="cc09a-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="cc09a-112">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="cc09a-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="cc09a-113">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> görüntüyü Pano'dan alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc09a-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="cc09a-114">Bu örnek görüntüyü Pano'ya almadan ve atanarak önce olup olmadığını denetler `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="cc09a-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 <span data-ttu-id="cc09a-115">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc09a-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="cc09a-116">Kod parçacığı Seçici bulunur **Windows Forms uygulamaları > Pano**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="cc09a-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="cc09a-117">Uygulamayı kapatmak bile sonra Pano'ya yerleştirilen öğelerin korunur.</span><span class="sxs-lookup"><span data-stu-id="cc09a-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="cc09a-118">Pano'da depolanan dosya türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="cc09a-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="cc09a-119">Panodaki veriler birkaç metin, ses dosyası veya bir görüntü gibi farklı form alabilir.</span><span class="sxs-lookup"><span data-stu-id="cc09a-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="cc09a-120">Ne tür bir dosya Pano'ya olduğunu belirlemek için yöntemleri gibi kullanabilir <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc09a-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="cc09a-121"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Yöntemi denetlemek istediğiniz özel bir biçim varsa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc09a-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="cc09a-122">Kullanım `ContainsImage` Pano'ya bulunan verileri görüntüyü olup olmadığını belirlemek için işlev.</span><span class="sxs-lookup"><span data-stu-id="cc09a-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="cc09a-123">Aşağıdaki kod, verileri bir görüntü ve buna göre raporlar olup olmadığını görmek için denetler.</span><span class="sxs-lookup"><span data-stu-id="cc09a-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="cc09a-124">Pano temizleme</span><span class="sxs-lookup"><span data-stu-id="cc09a-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="cc09a-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Yöntemi Pano temizler.</span><span class="sxs-lookup"><span data-stu-id="cc09a-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="cc09a-126">Pano başka işlemler tarafından paylaşıldığından, temizlemeden bu işlemleri üzerinde bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc09a-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="cc09a-127">Aşağıdaki kodu nasıl kullanılacağını gösterir `Clear` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc09a-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="cc09a-128">Panoya yazma</span><span class="sxs-lookup"><span data-stu-id="cc09a-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="cc09a-129">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metni panoya yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="cc09a-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="cc09a-130">Aşağıdaki kod, "Bu bir test panoya dizedir" dizesi yazar.</span><span class="sxs-lookup"><span data-stu-id="cc09a-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 <span data-ttu-id="cc09a-131">`SetText` Yöntemi türü içeren bir biçim parametresini kabul edebileceği <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="cc09a-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="cc09a-132">Aşağıdaki kod, "Bu bir test panoya RTF metin olarak dizedir" dizesi yazar.</span><span class="sxs-lookup"><span data-stu-id="cc09a-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 <span data-ttu-id="cc09a-133">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> panoya veri yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="cc09a-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="cc09a-134">Bu örnek Yazar `DataObject``dataChunk` özel biçim Pano'ya `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="cc09a-134">This example writes the `DataObject``dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 <span data-ttu-id="cc09a-135">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> panoya ses veri yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="cc09a-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="cc09a-136">Bu örnek, bayt dizisi oluşturur `musicReader`, dosyasını okur `cool.wav` , içine ve panoya yazar.</span><span class="sxs-lookup"><span data-stu-id="cc09a-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc09a-137">Pano diğer kullanıcılar tarafından erişilebilir olduğundan, parolalar veya gizli verileri gibi hassas bilgileri depolamak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="cc09a-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc09a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc09a-138">See also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [<span data-ttu-id="cc09a-139">Nasıl yapılır: nesne verilerini bir XML dosyasından okuma</span><span class="sxs-lookup"><span data-stu-id="cc09a-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="cc09a-140">Nasıl yapılır: nesne verilerini bir XML dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="cc09a-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
