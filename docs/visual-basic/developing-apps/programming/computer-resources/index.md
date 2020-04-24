---
title: Bilgisayar kaynaklarına erişme
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 27310a50289b9b2c315f52ad471da1f32ef0721a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345531"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="5804d-102">Bilgisayar kaynaklarına erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5804d-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="5804d-103">`My.Computer` Nesne, içindeki `My`üç merkezi nesneden biridir, bilgilere ve yaygın olarak kullanılan işlevlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5804d-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="5804d-104">`My.Computer`uygulamanın çalıştığı bilgisayara erişmek için yöntemler, Özellikler ve olaylar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5804d-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="5804d-105">Nesneleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="5804d-105">Its objects include:</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <span data-ttu-id="5804d-106">Pano (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="5804d-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <span data-ttu-id="5804d-107">Kayıt defteri<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>()</span><span class="sxs-lookup"><span data-stu-id="5804d-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5804d-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="5804d-108">In this section</span></span>

[<span data-ttu-id="5804d-109">Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="5804d-109">Playing Sounds</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md)  
<span data-ttu-id="5804d-110">Arka planda bir ses `My.Computer.Audio`çalmak gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5804d-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

[<span data-ttu-id="5804d-111">Verileri Panoda Depolama ve Panodan Okuma</span><span class="sxs-lookup"><span data-stu-id="5804d-111">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)  
<span data-ttu-id="5804d-112">İle `My.Computer.Clipboard`ilişkili görevleri (örneğin, panodaki verileri okuma veya verileri yazma gibi) listeler.</span><span class="sxs-lookup"><span data-stu-id="5804d-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

[<span data-ttu-id="5804d-113">Bilgisayar Hakkında Bilgi Alma</span><span class="sxs-lookup"><span data-stu-id="5804d-113">Getting Information about the Computer</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md)  
<span data-ttu-id="5804d-114">Bir bilgisayarın tam adını `My.Computer.Info`veya IP adreslerini belirleme gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5804d-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

[<span data-ttu-id="5804d-115">Klavyeye Erişme</span><span class="sxs-lookup"><span data-stu-id="5804d-115">Accessing the Keyboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
<span data-ttu-id="5804d-116">İle `My.Computer.Keyboard`ilişkili görevleri listeler, örneğin CAPS LOCK açık olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="5804d-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

[<span data-ttu-id="5804d-117">Fareye Erişme</span><span class="sxs-lookup"><span data-stu-id="5804d-117">Accessing the Mouse</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md)  
<span data-ttu-id="5804d-118">Bir farenin mevcut olup `My.Computer.Mouse`olmadığını belirleme gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5804d-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

[<span data-ttu-id="5804d-119">Ağ İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5804d-119">Performing Network Operations</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md)  
<span data-ttu-id="5804d-120">Dosya yükleme veya indirme `My.Computer.Network`gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5804d-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

[<span data-ttu-id="5804d-121">Bilgisayar Bağlantı Noktalarına Erişme</span><span class="sxs-lookup"><span data-stu-id="5804d-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)  
<span data-ttu-id="5804d-122">Kullanılabilir seri bağlantı noktalarını `My.Computer.Ports`gösterme veya seri bağlantı noktalarına dizeler gönderme gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5804d-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

[<span data-ttu-id="5804d-123">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="5804d-123">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
<span data-ttu-id="5804d-124">Kayıt defteri anahtarlarına veri `My.Computer.Registry`okuma veya verileri yazma gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5804d-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
