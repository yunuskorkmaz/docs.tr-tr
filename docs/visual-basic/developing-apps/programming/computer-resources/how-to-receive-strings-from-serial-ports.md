---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345592"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="88a53-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="88a53-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="88a53-103">Bu konuda, Visual Basic bilgisayarın seri bağlantı noktalarından dizeler almak için `My.Computer.Ports` nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88a53-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="88a53-104">Seri bağlantı noktasından dizeler almak için</span><span class="sxs-lookup"><span data-stu-id="88a53-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="88a53-105">Dönüş dizesini başlatın.</span><span class="sxs-lookup"><span data-stu-id="88a53-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="88a53-106">Dizelerin hangi seri bağlantı noktası tarafından sağlanması gerektiğini saptayın.</span><span class="sxs-lookup"><span data-stu-id="88a53-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="88a53-107">Bu örnek `COM1`olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="88a53-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="88a53-108">Bağlantı noktasına bir başvuru almak için `My.Computer.Ports.OpenSerialPort` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a53-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="88a53-109">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="88a53-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="88a53-110">`Try...Catch...Finally` bloğu, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="88a53-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="88a53-111">Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="88a53-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="88a53-112">Daha fazla satır kullanılamadığından metin satırlarını okumak için bir `Do` döngüsü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="88a53-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="88a53-113">Seri bağlantı noktasından sonraki kullanılabilir metin satırını okumak için <xref:System.IO.Ports.SerialPort.ReadLine> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a53-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="88a53-114"><xref:System.IO.Ports.SerialPort.ReadLine> yönteminin `Nothing` döndürüp döndürmediğine (daha fazla metin kullanılamadığı anlamına gelir) `If` bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a53-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="88a53-115">`Nothing`döndürmesi durumunda `Do` döngüsünden çıkın.</span><span class="sxs-lookup"><span data-stu-id="88a53-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="88a53-116">Dize gerçekten okuneyse, durumu işlemek için `If` ifadesine `Else` bloğu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88a53-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="88a53-117">Blok, dizeyi seri bağlantı noktasından dönüş dizesine ekler.</span><span class="sxs-lookup"><span data-stu-id="88a53-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="88a53-118">Dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="88a53-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="88a53-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="88a53-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="88a53-120">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88a53-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="88a53-121">Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="88a53-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="88a53-122">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="88a53-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88a53-123">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="88a53-123">Compiling the Code</span></span>  

 <span data-ttu-id="88a53-124">Bu örnek, bilgisayarın `COM1`kullandığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="88a53-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="88a53-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="88a53-125">Robust Programming</span></span>  

 <span data-ttu-id="88a53-126">Bu örnek, bilgisayarın `COM1`kullandığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="88a53-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="88a53-127">Daha fazla esneklik için, kod kullanıcının kullanılabilir bağlantı noktası listesinden istenen seri bağlantı noktasını seçmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="88a53-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="88a53-128">Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="88a53-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="88a53-129">Bu örnek, uygulamanın bağlantı noktasını kapatıp zaman aşımı özel durumlarını yakalamada emin olmak için bir `Try...Catch...Finally` bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="88a53-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="88a53-130">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88a53-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a53-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88a53-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="88a53-132">Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="88a53-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="88a53-133">Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="88a53-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="88a53-134">Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="88a53-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
