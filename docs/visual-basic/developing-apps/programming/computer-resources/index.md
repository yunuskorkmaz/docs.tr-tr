---
title: Bilgisayar kaynaklarına erişme
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 9595abaa1daa2b4a4436577d58856183dcb4d9ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401790"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="6ffee-102">Bilgisayar kaynaklarına erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ffee-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="6ffee-103">`My.Computer`Nesne, içindeki üç merkezi nesneden biridir `My` , bilgilere ve yaygın olarak kullanılan işlevlere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ffee-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="6ffee-104">`My.Computer`uygulamanın çalıştığı bilgisayara erişmek için yöntemler, Özellikler ve olaylar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ffee-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="6ffee-105">Nesneleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="6ffee-105">Its objects include:</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <span data-ttu-id="6ffee-106">Pano ( <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy> )</span><span class="sxs-lookup"><span data-stu-id="6ffee-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
- <xref:Microsoft.VisualBasic.Devices.Clock>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
- <xref:Microsoft.VisualBasic.Devices.Keyboard>
- <xref:Microsoft.VisualBasic.Devices.Mouse>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <span data-ttu-id="6ffee-107">Kayıt defteri ( <xref:Microsoft.VisualBasic.MyServices.RegistryProxy> )</span><span class="sxs-lookup"><span data-stu-id="6ffee-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6ffee-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="6ffee-108">In this section</span></span>

[<span data-ttu-id="6ffee-109">Ses Çalma</span><span class="sxs-lookup"><span data-stu-id="6ffee-109">Playing Sounds</span></span>](playing-sounds.md)  
<span data-ttu-id="6ffee-110">`My.Computer.Audio`Arka planda bir ses çalmak gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="6ffee-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

[<span data-ttu-id="6ffee-111">Verileri Panoda Depolama ve Panodan Okuma</span><span class="sxs-lookup"><span data-stu-id="6ffee-111">Storing Data to and Reading from the Clipboard</span></span>](storing-data-to-and-reading-from-the-clipboard.md)  
<span data-ttu-id="6ffee-112">İle ilişkili görevleri ( `My.Computer.Clipboard` Örneğin, panodaki verileri okuma veya verileri yazma gibi) listeler.</span><span class="sxs-lookup"><span data-stu-id="6ffee-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

[<span data-ttu-id="6ffee-113">Bilgisayar Hakkında Bilgi Alma</span><span class="sxs-lookup"><span data-stu-id="6ffee-113">Getting Information about the Computer</span></span>](getting-information-about-the-computer.md)  
<span data-ttu-id="6ffee-114">`My.Computer.Info`Bir bilgisayarın tam adını veya IP adreslerini belirleme gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="6ffee-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

[<span data-ttu-id="6ffee-115">Klavyeye Erişme</span><span class="sxs-lookup"><span data-stu-id="6ffee-115">Accessing the Keyboard</span></span>](accessing-the-keyboard.md)  
<span data-ttu-id="6ffee-116">İle ilişkili görevleri listeler `My.Computer.Keyboard` , örneğin CAPS LOCK açık olup olmadığını belirleme.</span><span class="sxs-lookup"><span data-stu-id="6ffee-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

[<span data-ttu-id="6ffee-117">Fareye Erişme</span><span class="sxs-lookup"><span data-stu-id="6ffee-117">Accessing the Mouse</span></span>](accessing-the-mouse.md)  
<span data-ttu-id="6ffee-118">`My.Computer.Mouse`Bir farenin mevcut olup olmadığını belirleme gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="6ffee-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

[<span data-ttu-id="6ffee-119">Ağ İşlemlerini Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6ffee-119">Performing Network Operations</span></span>](performing-network-operations.md)  
<span data-ttu-id="6ffee-120">Dosya yükleme veya indirme gibi ile ilişkili görevleri listeler `My.Computer.Network` .</span><span class="sxs-lookup"><span data-stu-id="6ffee-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

[<span data-ttu-id="6ffee-121">Bilgisayar Bağlantı Noktalarına Erişme</span><span class="sxs-lookup"><span data-stu-id="6ffee-121">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)  
<span data-ttu-id="6ffee-122">`My.Computer.Ports`Kullanılabilir seri bağlantı noktalarını gösterme veya seri bağlantı noktalarına dizeler gönderme gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="6ffee-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

[<span data-ttu-id="6ffee-123">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="6ffee-123">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)  
<span data-ttu-id="6ffee-124">`My.Computer.Registry`Kayıt defteri anahtarlarına veri okuma veya verileri yazma gibi ile ilişkili görevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="6ffee-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>
