---
title: 'Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: e55ce6399dae435fbd5b2f730d4d0848c98d8955
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363273"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="87eee-102">Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Ekli Modemleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="87eee-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="87eee-103">Bu konu başlığı `My.Computer.Ports` altında, Visual Basic bir modem aramak için nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87eee-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="87eee-104">Genellikle, modem bilgisayardaki seri bağlantı noktalarından birine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="87eee-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="87eee-105">Uygulamanızın modemle iletişim kurması için uygun seri bağlantı noktasına komut göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="87eee-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="87eee-106">Modem aramak için</span><span class="sxs-lookup"><span data-stu-id="87eee-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="87eee-107">Modemin bağlandığı seri bağlantı noktasını belirleme.</span><span class="sxs-lookup"><span data-stu-id="87eee-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="87eee-108">Bu örnek, modemin COM1 üzerinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="87eee-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="87eee-109">`My.Computer.Ports.OpenSerialPort`Bağlantı noktasına bir başvuru almak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="87eee-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="87eee-110">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="87eee-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="87eee-111">`Using`Blok, uygulamanın bir özel durum oluşturursa bile seri bağlantı noktasını kapatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="87eee-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="87eee-112">Seri bağlantı noktasını işleyen tüm kodlar bu blok içinde veya bir blok içinde görünmelidir `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="87eee-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="87eee-113">Özelliği, `DtrEnable` bilgisayarın modemden gelen bir iletimi kabul etmeye hazırlandığını belirtecek şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87eee-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="87eee-114">Arama komutunu ve telefon numarasını, yöntemi aracılığıyla seri bağlantı noktası üzerinden modeme gönderin <xref:System.IO.Ports.SerialPort.Write%2A> .</span><span class="sxs-lookup"><span data-stu-id="87eee-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="87eee-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="87eee-115">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="87eee-116">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87eee-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="87eee-117">Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="87eee-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="87eee-118">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="87eee-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87eee-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="87eee-119">Compiling the Code</span></span>  

 <span data-ttu-id="87eee-120">Bu örnek ad alanına bir başvuru gerektirir <xref:System?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="87eee-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="87eee-121">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="87eee-121">Robust Programming</span></span>  

 <span data-ttu-id="87eee-122">Bu örnek, modemin COM1 'ya bağlı olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="87eee-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="87eee-123">Kodunuzun, kullanıcının kullanılabilir bağlantı noktaları listesinden istenen seri bağlantı noktasını seçmesine izin vermeyi öneririz.</span><span class="sxs-lookup"><span data-stu-id="87eee-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="87eee-124">Daha fazla bilgi için bkz. [nasıl yapılır: kullanılabilir seri bağlantı noktalarını gösterme](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="87eee-124">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="87eee-125">Bu örnek, bir `Using` özel durum oluşturursa uygulamanın bağlantı noktasını kapatdığından emin olmak için bir bloğu kullanır.</span><span class="sxs-lookup"><span data-stu-id="87eee-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="87eee-126">Daha fazla bilgi için bkz. [using deyimleri](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="87eee-126">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="87eee-127">Bu örnekte, uygulama, modemi çevirdikten sonra seri bağlantı noktasının bağlantısını keser.</span><span class="sxs-lookup"><span data-stu-id="87eee-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="87eee-128">Gerçekçi olarak, modemden veya modemden veri aktarmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="87eee-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="87eee-129">Daha fazla bilgi için bkz. [nasıl yapılır: seri bağlantı noktalarından dize alma](how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="87eee-129">For more information, see [How to: Receive Strings From Serial Ports](how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87eee-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87eee-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="87eee-131">Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme</span><span class="sxs-lookup"><span data-stu-id="87eee-131">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="87eee-132">Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma</span><span class="sxs-lookup"><span data-stu-id="87eee-132">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="87eee-133">Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="87eee-133">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
