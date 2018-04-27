---
title: "Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma"
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76124654e479ae84702524d68bcced34610d1526
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="87263-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="87263-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="87263-103">Bu konuda nasıl kullanılacağını açıklar `My.Computer.Ports` bilgisayarın Visual Basic'te seri bağlantı noktalarından dize alma için.</span><span class="sxs-lookup"><span data-stu-id="87263-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="87263-104">Seri bağlantı noktasından dizeleri almak için</span><span class="sxs-lookup"><span data-stu-id="87263-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="87263-105">Dönüş dizesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="87263-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  <span data-ttu-id="87263-106">Hangi seri bağlantı dizeleri sağlamalıdır belirler.</span><span class="sxs-lookup"><span data-stu-id="87263-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="87263-107">Bu örnekte olduğu varsayılır `COM1`.</span><span class="sxs-lookup"><span data-stu-id="87263-107">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="87263-108">Kullanım `My.Computer.Ports.OpenSerialPort` bir başvuru noktasına elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="87263-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="87263-109">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="87263-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="87263-110">`Try...Catch...Finally` Bloğu bir özel durum oluşturursa bile seri bağlantı noktasını kapatmak uygulama izin verir.</span><span class="sxs-lookup"><span data-stu-id="87263-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="87263-111">Seri bağlantı noktası yöneten tüm kod bu blokta görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="87263-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="87263-112">Oluşturma bir `Do` daha fazla satır kullanılabilir oluncaya kadar satırlık metin okumak için döngü.</span><span class="sxs-lookup"><span data-stu-id="87263-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  <span data-ttu-id="87263-113">Kullanım <xref:System.IO.Ports.SerialPort.ReadLine> metnin kullanılabilen bir sonraki satıra seri bağlantı noktasından okumak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="87263-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  <span data-ttu-id="87263-114">Kullanım bir `If` belirlemek için deyimi <xref:System.IO.Ports.SerialPort.ReadLine> yöntemi döndürür `Nothing` (daha fazla metin başka bir deyişle, kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="87263-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="87263-115">Bunu döndürürse `Nothing`, çıkış `Do` döngü.</span><span class="sxs-lookup"><span data-stu-id="87263-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  <span data-ttu-id="87263-116">Ekleme bir `Else` için engelleyin `If` dize gerçekte salt okunur ise durumu işlemek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="87263-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="87263-117">Blok seri bağlantı noktasından dizesi Dönüş dizesi olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="87263-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  <span data-ttu-id="87263-118">Dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="87263-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="87263-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="87263-119">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 <span data-ttu-id="87263-120">Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87263-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="87263-121">Kod parçacığı Seçici bulunur **bağlantısı ve ağ**.</span><span class="sxs-lookup"><span data-stu-id="87263-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="87263-122">Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="87263-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87263-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="87263-123">Compiling the Code</span></span>  
 <span data-ttu-id="87263-124">Bu örnek kullandığınızı varsayar `COM1`.</span><span class="sxs-lookup"><span data-stu-id="87263-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="87263-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="87263-125">Robust Programming</span></span>  
 <span data-ttu-id="87263-126">Bu örnek kullandığınızı varsayar `COM1`.</span><span class="sxs-lookup"><span data-stu-id="87263-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="87263-127">Daha fazla esneklik için kod kullanıcının istenen seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçmesine izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="87263-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="87263-128">Daha fazla bilgi için bkz: [nasıl yapılır: kullanılabilir seri bağlantı noktalarını göster](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="87263-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="87263-129">Bu örnekte bir `Try...Catch...Finally` blok uygulama bağlantı noktasını kapatır emin olmak ve hiçbir zaman aşımı özel durumları yakalamak için.</span><span class="sxs-lookup"><span data-stu-id="87263-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="87263-130">Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="87263-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87263-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87263-131">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="87263-132">Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="87263-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="87263-133">Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="87263-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="87263-134">Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="87263-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
