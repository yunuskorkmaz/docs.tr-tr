---
title: Verileri Panoda depolama ve panodan (Visual Basic) okuma
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 19d0fcafb76c40a00939de59968dfaf2e6bd683c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921309"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="c74bf-102">Verileri Panoda depolama ve panodan (Visual Basic) okuma</span><span class="sxs-lookup"><span data-stu-id="c74bf-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>
<span data-ttu-id="c74bf-103">Pano, metin ve görüntü gibi verileri depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c74bf-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="c74bf-104">Tüm etkin işlemler tarafından Pano paylaşıldığından, bunlar arasında veri aktarmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c74bf-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="c74bf-105">`My.Computer.Clipboard` Nesne kolayca panoya erişebilir ve okuma ve yazma olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c74bf-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="c74bf-106">Panodan okuma</span><span class="sxs-lookup"><span data-stu-id="c74bf-106">Reading from the Clipboard</span></span>  
 <span data-ttu-id="c74bf-107">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> Pano metni okumak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="c74bf-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="c74bf-108">Aşağıdaki kod okur ve bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c74bf-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="c74bf-109">Örneğin düzgün çalışması Panodaki depolanan metin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c74bf-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="c74bf-110">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c74bf-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c74bf-111">Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Pano**.</span><span class="sxs-lookup"><span data-stu-id="c74bf-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="c74bf-112">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c74bf-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="c74bf-113">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> panodan bir görüntü almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c74bf-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="c74bf-114">Bu örnekte görüntüyü Pano'ya alınması ve giderek önce olup olmadığını denetler `PictureBox1`.</span><span class="sxs-lookup"><span data-stu-id="c74bf-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="c74bf-115">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c74bf-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c74bf-116">Kod parçacığı Seçici'de bulunur **Windows Forms uygulamaları > Pano**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c74bf-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="c74bf-117">Uygulama kapatma bile sonra Panoda yerleştirilen öğelerin açık kalır.</span><span class="sxs-lookup"><span data-stu-id="c74bf-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="c74bf-118">Panoya depolanan dosya türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="c74bf-118">Determining the type of file stored in the Clipboard</span></span>  
 <span data-ttu-id="c74bf-119">Panodaki veriler, birkaç metin, ses dosyası ve görüntü gibi farklı form alabilir.</span><span class="sxs-lookup"><span data-stu-id="c74bf-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="c74bf-120">Ne tür bir dosya olup Panodaki belirlemek için yöntemleri gibi kullanabileceğiniz <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="c74bf-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="c74bf-121"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Yöntemi kontrol etmek istediğiniz özel bir biçim varsa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c74bf-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="c74bf-122">Kullanım `ContainsImage` verileri Panoya bir görüntü olup olmadığını belirlemek için işlevi.</span><span class="sxs-lookup"><span data-stu-id="c74bf-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="c74bf-123">Veriler bir görüntü ve buna göre raporları görmek için aşağıdaki kodu denetler.</span><span class="sxs-lookup"><span data-stu-id="c74bf-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="c74bf-124">Pano temizleme</span><span class="sxs-lookup"><span data-stu-id="c74bf-124">Clearing the Clipboard</span></span>  
 <span data-ttu-id="c74bf-125"><xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Yöntemi Pano temizler.</span><span class="sxs-lookup"><span data-stu-id="c74bf-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="c74bf-126">Pano başka işlemler tarafından paylaşıldığından, temizlemeden bu işlemlerin bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="c74bf-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="c74bf-127">Aşağıdaki kod nasıl kullanılacağını gösterir `Clear` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c74bf-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="c74bf-128">Pano yazma</span><span class="sxs-lookup"><span data-stu-id="c74bf-128">Writing to the Clipboard</span></span>  
 <span data-ttu-id="c74bf-129">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> panoya metin yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c74bf-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="c74bf-130">Aşağıdaki kod, "Bu bir test panoya dizedir" dizesi yazar.</span><span class="sxs-lookup"><span data-stu-id="c74bf-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="c74bf-131">`SetText` Yöntemi, bir tür içeren bir biçim parametresini kabul edebilir <xref:System.Windows.Forms.TextDataFormat>.</span><span class="sxs-lookup"><span data-stu-id="c74bf-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="c74bf-132">Aşağıdaki kod, "Bu bir test RTF metin olarak panoya dizedir" dizesi yazar.</span><span class="sxs-lookup"><span data-stu-id="c74bf-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="c74bf-133">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> panoya veri yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c74bf-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="c74bf-134">Bu örnek, Yazar `DataObject` `dataChunk` özel biçiminde panoya `specialFormat`.</span><span class="sxs-lookup"><span data-stu-id="c74bf-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="c74bf-135">Kullanım <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> panoya ses veri yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c74bf-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="c74bf-136">Bu örnek, bir bayt dizisi oluşturur `musicReader`, dosyayı okur `cool.wav` içine ve panoya yazar.</span><span class="sxs-lookup"><span data-stu-id="c74bf-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="c74bf-137">Pano, diğer kullanıcılar tarafından erişilebilir olduğundan, parolalar veya gizli verileri gibi hassas bilgileri depolamak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="c74bf-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74bf-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c74bf-138">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="c74bf-139">Nasıl yapılır: Nesne verilerini bir XML dosyasından okuma</span><span class="sxs-lookup"><span data-stu-id="c74bf-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="c74bf-140">Nasıl yapılır: Nesne verilerini bir XML dosyasına yazma</span><span class="sxs-lookup"><span data-stu-id="c74bf-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
