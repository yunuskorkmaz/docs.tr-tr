---
title: .NET 'teki kanal Işlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706562"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="5b4b1-102">.NET 'teki kanal Işlemleri</span><span class="sxs-lookup"><span data-stu-id="5b4b1-102">Pipe Operations in .NET</span></span>
<span data-ttu-id="5b4b1-103">Kanallar, işlemler arası iletişim için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="5b4b1-104">İki tür kanal vardır:</span><span class="sxs-lookup"><span data-stu-id="5b4b1-104">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="5b4b1-105">Anonim kanallar.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="5b4b1-106">Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="5b4b1-107">Anonim kanallar, adlandırılmış kanallara göre daha az ek yük gerektirir, ancak sınırlı hizmetler sunar.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="5b4b1-108">Anonim kanallar tek yönlü ve ağ üzerinden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="5b4b1-109">Yalnızca tek bir sunucu örneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-109">They support only a single server instance.</span></span> <span data-ttu-id="5b4b1-110">Anonim kanallar, iş parçacıkları arasındaki iletişim için veya kanal tutamaçlarının oluşturulduğu sırada alt işleme kolayca geçirilebileceği üst ve alt işlemler arasında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="5b4b1-111">.NET ' te, <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıfları kullanarak anonim kanallar uygulayacağız.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-111">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="5b4b1-112">Bkz. [nasıl yapılır: yerel Işlemler arası iletişim Için anonim kanallar kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="5b4b1-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="5b4b1-113">Adlandırılmış kanallar.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-113">Named pipes.</span></span>  
  
     <span data-ttu-id="5b4b1-114">Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="5b4b1-115">Adlandırılmış kanallar tek yönlü veya çift yönlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="5b4b1-116">İleti tabanlı iletişimi destekler ve aynı kanal adını kullanarak birden fazla istemcinin sunucu işlemine aynı anda bağlanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="5b4b1-117">Adlandırılmış Kanallar, kimliğe bürünme özelliğini de destekler ve bu sayede, uzak sunucularda kendi izinlerini kullanmak üzere bağlantı kurma işlemi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="5b4b1-118">.NET ' te, adlandırılmış kanalları <xref:System.IO.Pipes.NamedPipeServerStream> ve <xref:System.IO.Pipes.NamedPipeClientStream> sınıfları kullanarak uygularmış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-118">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="5b4b1-119">Bkz. [nasıl yapılır: ağ Işlem iletişimi Için adlandırılmış kanalları kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="5b4b1-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b4b1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b4b1-120">See also</span></span>

- [<span data-ttu-id="5b4b1-121">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="5b4b1-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="5b4b1-122">Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="5b4b1-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="5b4b1-123">Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="5b4b1-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
