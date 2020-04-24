---
title: 'Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma'
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
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="114e0-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="114e0-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="114e0-103">Bu konu başlığı altında, bilgisayarın `My.Computer.Ports` seri bağlantı noktalarından Visual Basic dize almak için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="114e0-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="114e0-104">Seri bağlantı noktasından dizeler almak için</span><span class="sxs-lookup"><span data-stu-id="114e0-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="114e0-105">Dönüş dizesini başlatın.</span><span class="sxs-lookup"><span data-stu-id="114e0-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="114e0-106">Dizelerin hangi seri bağlantı noktası tarafından sağlanması gerektiğini saptayın.</span><span class="sxs-lookup"><span data-stu-id="114e0-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="114e0-107">Bu örnek, `COM1`olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="114e0-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="114e0-108">Bağlantı noktasına `My.Computer.Ports.OpenSerialPort` bir başvuru almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="114e0-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="114e0-109">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="114e0-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="114e0-110">`Try...Catch...Finally` Blok, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="114e0-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="114e0-111">Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="114e0-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="114e0-112">Daha fazla `Do` satır yoksa metin satırlarını okumak için bir döngü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="114e0-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="114e0-113">Seri bağlantı <xref:System.IO.Ports.SerialPort.ReadLine> noktasından sonraki kullanılabilir metin satırını okumak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="114e0-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="114e0-114">Yöntemin döndürüp `If` döndürmediğine `Nothing` yönelik bir ifade kullanın (yani daha fazla metin kullanılamaz). <xref:System.IO.Ports.SerialPort.ReadLine></span><span class="sxs-lookup"><span data-stu-id="114e0-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="114e0-115">Geri dönemezse `Nothing` `Do` döngüden çıkın.</span><span class="sxs-lookup"><span data-stu-id="114e0-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="114e0-116">Dize gerçekten `Else` okuneyse, `If` durumu işlemek için deyime bir blok ekleyin.</span><span class="sxs-lookup"><span data-stu-id="114e0-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="114e0-117">Blok, dizeyi seri bağlantı noktasından dönüş dizesine ekler.</span><span class="sxs-lookup"><span data-stu-id="114e0-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="114e0-118">Dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="114e0-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="114e0-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="114e0-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="114e0-120">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="114e0-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="114e0-121">Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="114e0-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="114e0-122">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="114e0-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="114e0-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="114e0-123">Compiling the Code</span></span>  

 <span data-ttu-id="114e0-124">Bu örnekte, bilgisayarın kullandığı `COM1`varsayılır.</span><span class="sxs-lookup"><span data-stu-id="114e0-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="114e0-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="114e0-125">Robust Programming</span></span>  

 <span data-ttu-id="114e0-126">Bu örnekte, bilgisayarın kullandığı `COM1`varsayılır.</span><span class="sxs-lookup"><span data-stu-id="114e0-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="114e0-127">Daha fazla esneklik için, kod kullanıcının kullanılabilir bağlantı noktası listesinden istenen seri bağlantı noktasını seçmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="114e0-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="114e0-128">Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="114e0-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="114e0-129">Bu örnek, uygulamanın `Try...Catch...Finally` bağlantı noktasını kapatıp zaman aşımı özel durumlarını yakalamada emin olmak için bir bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="114e0-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="114e0-130">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="114e0-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114e0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="114e0-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="114e0-132">Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="114e0-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="114e0-133">Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="114e0-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="114e0-134">Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="114e0-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
