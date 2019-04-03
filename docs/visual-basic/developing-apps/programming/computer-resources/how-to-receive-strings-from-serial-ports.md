---
title: "Nasıl yapılır: Visual Basic'te seri bağlantı noktalarından dize alma"
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 1a7aa88cfb90f347caed24bec0b5123dafb4c533
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822849"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="75638-102">Nasıl yapılır: Visual Basic'te seri bağlantı noktalarından dize alma</span><span class="sxs-lookup"><span data-stu-id="75638-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="75638-103">Bu konu nasıl kullanılacağını açıklar `My.Computer.Ports` bilgisayarın Visual Basic'te seri bağlantı noktalarından dize alma için.</span><span class="sxs-lookup"><span data-stu-id="75638-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="75638-104">Seri bağlantı noktasından dizelerini almak için</span><span class="sxs-lookup"><span data-stu-id="75638-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="75638-105">Dönüş dizesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="75638-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2.  <span data-ttu-id="75638-106">Hangi seri bağlantı dizeleri sağlamalıdır belirleyin.</span><span class="sxs-lookup"><span data-stu-id="75638-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="75638-107">Bu örnekte olduğu varsayılır `COM1`.</span><span class="sxs-lookup"><span data-stu-id="75638-107">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="75638-108">Kullanım `My.Computer.Ports.OpenSerialPort` bağlantı noktasına bir başvuru almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="75638-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="75638-109">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="75638-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="75638-110">`Try...Catch...Finally` Blok bile bir özel durum oluşturur seri bağlantı noktası kapatmak uygulama izin verir.</span><span class="sxs-lookup"><span data-stu-id="75638-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="75638-111">Seri bağlantı noktası yöneten tüm kod bu blok içinde görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="75638-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4.  <span data-ttu-id="75638-112">Oluşturma bir `Do` satırlık metin okuma için daha fazla satır kullanılabilir olana kadar döngü.</span><span class="sxs-lookup"><span data-stu-id="75638-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5.  <span data-ttu-id="75638-113">Kullanım <xref:System.IO.Ports.SerialPort.ReadLine> metin kullanılabilen bir sonraki satıra seri bağlantı noktasından okumak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="75638-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6.  <span data-ttu-id="75638-114">Kullanım bir `If` belirlemek için deyimi <xref:System.IO.Ports.SerialPort.ReadLine> yöntemi döndürür `Nothing` (yani daha fazla metin kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="75638-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="75638-115">Dönüş yaparsa `Nothing`, çıkış `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="75638-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7.  <span data-ttu-id="75638-116">Ekleme bir `Else` bloğunu `If` dize gerçekten salt okunur ise, durumu işlemek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="75638-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="75638-117">Blok seri bağlantı dizesinden dönüş dizesine ekler.</span><span class="sxs-lookup"><span data-stu-id="75638-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8.  <span data-ttu-id="75638-118">Dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="75638-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="75638-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="75638-119">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="75638-120">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75638-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="75638-121">Kod parçacığı Seçici'de bulunur **bağlantı ve ağ**.</span><span class="sxs-lookup"><span data-stu-id="75638-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="75638-122">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="75638-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75638-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="75638-123">Compiling the Code</span></span>  
 <span data-ttu-id="75638-124">Bu örnek kullandığınızı varsayar `COM1`.</span><span class="sxs-lookup"><span data-stu-id="75638-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="75638-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="75638-125">Robust Programming</span></span>  
 <span data-ttu-id="75638-126">Bu örnek kullandığınızı varsayar `COM1`.</span><span class="sxs-lookup"><span data-stu-id="75638-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="75638-127">Daha fazla esneklik için kodu, kullanıcının istenen seri bağlantı noktası kullanılabilir bağlantı noktaları bir listesinden seçmek izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="75638-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="75638-128">Daha fazla bilgi için [nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="75638-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="75638-129">Bu örnekte bir `Try...Catch...Finally` uygulama bağlantı noktasını kapatır emin olun ve herhangi bir zaman aşımı özel durumları yakalama bloğu.</span><span class="sxs-lookup"><span data-stu-id="75638-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="75638-130">Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="75638-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75638-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75638-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="75638-132">Nasıl yapılır: Seri bağlantı noktalarına ekli modemleri çevirme</span><span class="sxs-lookup"><span data-stu-id="75638-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="75638-133">Nasıl yapılır: Seri bağlantı noktalarına dizeler gönderme</span><span class="sxs-lookup"><span data-stu-id="75638-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="75638-134">Nasıl yapılır: Kullanılabilir seri bağlantı noktalarını gösterme</span><span class="sxs-lookup"><span data-stu-id="75638-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
