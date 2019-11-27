---
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
ms.openlocfilehash: 243fb237f3f9ba53f8b29079df08531c102c78dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349726"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="1de09-102">Verileri Panoda Depolama ve Panodan Okuma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1de09-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>

<span data-ttu-id="1de09-103">Pano, metin ve görüntü gibi verileri depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1de09-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="1de09-104">Pano tüm etkin süreçler tarafından paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1de09-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="1de09-105">`My.Computer.Clipboard` nesnesi, panoya kolayca erişmenizi ve bu dosyayı okuyup yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1de09-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="1de09-106">Panodan Okuma</span><span class="sxs-lookup"><span data-stu-id="1de09-106">Reading from the Clipboard</span></span>  

 <span data-ttu-id="1de09-107">Panodaki metni okumak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1de09-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="1de09-108">Aşağıdaki kod, metni okur ve bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1de09-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="1de09-109">Örneğin doğru şekilde çalışması için Panoda depolanan metin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1de09-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="1de09-110">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1de09-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="1de09-111">Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda**bulunur.</span><span class="sxs-lookup"><span data-stu-id="1de09-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="1de09-112">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="1de09-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="1de09-113">Panodan bir görüntü almak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1de09-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="1de09-114">Bu örnek, yüklemeden önce panoda bir görüntü olup olmadığını ve `PictureBox1`atamaya yönelik olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1de09-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="1de09-115">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1de09-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="1de09-116">Kod parçacığı seçicide, **pano > Windows Forms uygulamalarda**bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="1de09-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="1de09-117">Pano 'ya yerleştirilmiş öğeler, uygulama kapatıldıktan sonra bile kalır.</span><span class="sxs-lookup"><span data-stu-id="1de09-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="1de09-118">Panoda depolanan dosya türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="1de09-118">Determining the type of file stored in the Clipboard</span></span>  

 <span data-ttu-id="1de09-119">Panodaki veriler metin, ses dosyası veya görüntü gibi çeşitli biçimlerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="1de09-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="1de09-120">Panodaki dosya sıralamasını belirlemek için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>gibi yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1de09-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="1de09-121">Denetlemek istediğiniz özel bir biçim varsa <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> yöntemi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1de09-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="1de09-122">Panoda içerilen verilerin bir görüntü olup olmadığını anlamak için `ContainsImage` işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1de09-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="1de09-123">Aşağıdaki kod, verilerin bir görüntü ve raporların uygun olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1de09-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="1de09-124">Panoyu Temizleme</span><span class="sxs-lookup"><span data-stu-id="1de09-124">Clearing the Clipboard</span></span>  

 <span data-ttu-id="1de09-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> yöntemi panoyu temizler.</span><span class="sxs-lookup"><span data-stu-id="1de09-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="1de09-126">Pano başka süreçler tarafından paylaşıldığından, temizleme işlemi bu işlemlere etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1de09-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="1de09-127">Aşağıdaki kod `Clear` yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1de09-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="1de09-128">Panoya yazma</span><span class="sxs-lookup"><span data-stu-id="1de09-128">Writing to the Clipboard</span></span>  

 <span data-ttu-id="1de09-129">Panoya metin yazmak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1de09-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="1de09-130">Aşağıdaki kod, panoya "This bir test dizesidir" dizesini yazar.</span><span class="sxs-lookup"><span data-stu-id="1de09-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="1de09-131">`SetText` yöntemi bir <xref:System.Windows.Forms.TextDataFormat>türü içeren bir biçim parametresi kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="1de09-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="1de09-132">Aşağıdaki kod, "Bu bir test dizesi" dizesini RTF metni olarak panoya yazar.</span><span class="sxs-lookup"><span data-stu-id="1de09-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="1de09-133">Panoya veri yazmak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1de09-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="1de09-134">Bu örnek, `DataObject` `dataChunk` özel biçim `specialFormat`panoya yazar.</span><span class="sxs-lookup"><span data-stu-id="1de09-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="1de09-135">Pano 'ya ses verileri yazmak için <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1de09-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="1de09-136">Bu örnek, bayt dizisi `musicReader`oluşturur, dosyayı buna `cool.wav` okur ve sonra panoya yazar.</span><span class="sxs-lookup"><span data-stu-id="1de09-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> <span data-ttu-id="1de09-137">Panoya diğer kullanıcılar tarafından erişilebildiğinden, parola veya gizli veriler gibi hassas bilgileri depolamak için bu uygulamayı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="1de09-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de09-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1de09-138">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="1de09-139">Nasıl Yapılır: Nesne Verilerini bir XML Dosyasından Okuma</span><span class="sxs-lookup"><span data-stu-id="1de09-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="1de09-140">Nasıl Yapılır: Nesne Verilerini bir XML Dosyasına Yazma</span><span class="sxs-lookup"><span data-stu-id="1de09-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
