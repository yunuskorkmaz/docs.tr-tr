---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345592"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="7f993-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="7f993-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="7f993-103">Bu konu, Visual `My.Computer.Ports` Basic'te bilgisayarın seri bağlantı noktalarından dizeleri almak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7f993-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="7f993-104">Seri bağlantı noktasından dizeleri almak için</span><span class="sxs-lookup"><span data-stu-id="7f993-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="7f993-105">İade dizesini başlangıç olarak ver.</span><span class="sxs-lookup"><span data-stu-id="7f993-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="7f993-106">Dizeleri hangi seri bağlantı noktasısağlaması gerektiğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7f993-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="7f993-107">Bu örnek olduğunu `COM1`varsayar.</span><span class="sxs-lookup"><span data-stu-id="7f993-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="7f993-108">Bağlantı `My.Computer.Ports.OpenSerialPort` noktasına başvuruda bulunulmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f993-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="7f993-109">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="7f993-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="7f993-110">Blok, `Try...Catch...Finally` bir özel durum oluştursa bile uygulamanın seri bağlantı noktasını kapatmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7f993-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="7f993-111">Seri bağlantı noktasını işleyen tüm kodbu blok içinde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="7f993-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="7f993-112">Başka `Do` satır bulunana kadar metin satırlarını okumak için bir döngü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f993-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="7f993-113">Seri <xref:System.IO.Ports.SerialPort.ReadLine> bağlantı noktasından bir sonraki kullanılabilir metin satırını okumak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f993-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="7f993-114">Yöntemin `If` <xref:System.IO.Ports.SerialPort.ReadLine> geri döndüğünü `Nothing` belirlemek için bir deyim kullanın (bu da başka metin bulunmadığı anlamına gelir).</span><span class="sxs-lookup"><span data-stu-id="7f993-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="7f993-115">Dönerse, `Nothing`döngüden `Do` çıkın.</span><span class="sxs-lookup"><span data-stu-id="7f993-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="7f993-116">Dize `Else` `If` gerçekten okunuyorsa büyük/küçük harf işlemek için deyime bir blok ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7f993-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="7f993-117">Blok, dizeyi seri bağlantı noktasından return string'e ekler.</span><span class="sxs-lookup"><span data-stu-id="7f993-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="7f993-118">Dizeyi geri ver.</span><span class="sxs-lookup"><span data-stu-id="7f993-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="7f993-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f993-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="7f993-120">Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f993-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="7f993-121">Kod snippet toplayıcı, **bağlantı ve ağ**bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7f993-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="7f993-122">Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.</span><span class="sxs-lookup"><span data-stu-id="7f993-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f993-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7f993-123">Compiling the Code</span></span>  

 <span data-ttu-id="7f993-124">Bu örnek, bilgisayarın kullandığını `COM1`varsayar.</span><span class="sxs-lookup"><span data-stu-id="7f993-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7f993-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="7f993-125">Robust Programming</span></span>  

 <span data-ttu-id="7f993-126">Bu örnek, bilgisayarın kullandığını `COM1`varsayar.</span><span class="sxs-lookup"><span data-stu-id="7f993-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="7f993-127">Daha fazla esneklik için, kod kullanıcının kullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmesine izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="7f993-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="7f993-128">Daha fazla bilgi için [bkz: Kullanılabilir Seri Bağlantı Noktalarını Göster.](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)</span><span class="sxs-lookup"><span data-stu-id="7f993-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="7f993-129">Bu örnek, `Try...Catch...Finally` uygulamanın bağlantı noktasını kapattıklarından emin olmak ve zaman aralarını yakalamak için bir blok kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f993-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="7f993-130">Daha fazla bilgi için [bkz. Yakalamak... Son Olarak İfade](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7f993-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f993-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f993-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="7f993-132">Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="7f993-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="7f993-133">Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="7f993-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="7f993-134">Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="7f993-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
