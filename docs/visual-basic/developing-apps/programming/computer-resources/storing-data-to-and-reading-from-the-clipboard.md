---
description: 'Hakkında daha fazla bilgi edinin: panodaki verileri depolama ve okuma (Visual Basic)'
title: Verileri Panoda Depolama ve Panodan Okuma
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 18cb66f6d8093757ce34ddb20659824787460920
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666348"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="29779-103">Verileri Panoda Depolama ve Panodan Okuma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29779-103">Storing data to and reading from the Clipboard (Visual Basic)</span></span>

<span data-ttu-id="29779-104">Pano, metin ve görüntü gibi verileri depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29779-104">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="29779-105">Pano tüm etkin süreçler tarafından paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29779-105">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="29779-106">`My.Computer.Clipboard`Nesnesi panoya kolayca erişmenizi ve bu panoyu okuyup yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="29779-106">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="29779-107">Panodan Okuma</span><span class="sxs-lookup"><span data-stu-id="29779-107">Reading from the Clipboard</span></span>  

 <span data-ttu-id="29779-108"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A>Panodaki metni okumak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29779-108">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="29779-109">Aşağıdaki kod, metni okur ve bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="29779-109">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="29779-110">Örneğin doğru şekilde çalışması için Panoda depolanan metin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29779-110">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="29779-111">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29779-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="29779-112">Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda** bulunur.</span><span class="sxs-lookup"><span data-stu-id="29779-112">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="29779-113">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="29779-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="29779-114"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A>Panodan bir görüntü almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29779-114">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="29779-115">Bu örnek, yüklemeden önce panoda bir resim olup olmadığını ve üzerine atamayı denetler `PictureBox1` .</span><span class="sxs-lookup"><span data-stu-id="29779-115">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="29779-116">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29779-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="29779-117">Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda** bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="29779-117">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="29779-118">Pano 'ya yerleştirilmiş öğeler, uygulama kapatıldıktan sonra bile kalır.</span><span class="sxs-lookup"><span data-stu-id="29779-118">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="29779-119">Panoda depolanan dosya türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="29779-119">Determining the type of file stored in the Clipboard</span></span>  

 <span data-ttu-id="29779-120">Panodaki veriler metin, ses dosyası veya görüntü gibi çeşitli biçimlerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="29779-120">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="29779-121">Panodaki dosya sıralamasını belirlemek için,, ve gibi yöntemleri kullanabilirsiniz <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A> <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A> <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A> <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A> .</span><span class="sxs-lookup"><span data-stu-id="29779-121">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="29779-122"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A>Denetlemek istediğiniz özel bir biçim varsa yöntemi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29779-122">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="29779-123">`ContainsImage`Panoda bulunan verilerin bir görüntü olup olmadığını anlamak için işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29779-123">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="29779-124">Aşağıdaki kod, verilerin bir görüntü ve raporların uygun olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="29779-124">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="29779-125">Panoyu Temizleme</span><span class="sxs-lookup"><span data-stu-id="29779-125">Clearing the Clipboard</span></span>  

 <span data-ttu-id="29779-126"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A>Yöntemi panoyu temizler.</span><span class="sxs-lookup"><span data-stu-id="29779-126">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="29779-127">Pano başka süreçler tarafından paylaşıldığından, temizleme işlemi bu işlemlere etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="29779-127">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="29779-128">Aşağıdaki kod yönteminin nasıl kullanılacağını gösterir `Clear` .</span><span class="sxs-lookup"><span data-stu-id="29779-128">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="29779-129">Panoya yazma</span><span class="sxs-lookup"><span data-stu-id="29779-129">Writing to the Clipboard</span></span>  

 <span data-ttu-id="29779-130"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A>Panoya metin yazmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29779-130">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="29779-131">Aşağıdaki kod, panoya "This bir test dizesidir" dizesini yazar.</span><span class="sxs-lookup"><span data-stu-id="29779-131">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="29779-132">`SetText`Yöntemi, türü içeren bir biçim parametresini kabul edebilir <xref:System.Windows.Forms.TextDataFormat> .</span><span class="sxs-lookup"><span data-stu-id="29779-132">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="29779-133">Aşağıdaki kod, "Bu bir test dizesi" dizesini RTF metni olarak panoya yazar.</span><span class="sxs-lookup"><span data-stu-id="29779-133">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="29779-134"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A>Verileri panoya yazmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29779-134">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="29779-135">Bu örnek, öğesini `DataObject` `dataChunk` panoya özel biçimde yazar `specialFormat` .</span><span class="sxs-lookup"><span data-stu-id="29779-135">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="29779-136">Pano 'ya <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> ses verileri yazmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29779-136">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="29779-137">Bu örnek, Byte dizisini oluşturur `musicReader` , dosyayı onunla okur `cool.wav` ve panoya yazar.</span><span class="sxs-lookup"><span data-stu-id="29779-137">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> <span data-ttu-id="29779-138">Panoya diğer kullanıcılar tarafından erişilebildiğinden, parola veya gizli veriler gibi hassas bilgileri depolamak için bu uygulamayı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="29779-138">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29779-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29779-139">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="29779-140">Nasıl yapılır: bir XML dosyasından nesne verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="29779-140">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="29779-141">Nasıl yapılır: nesne verilerini bir XML dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="29779-141">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
