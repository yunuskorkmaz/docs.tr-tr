---
title: .NET 'teki kanal Işlemleri
description: ".NET 'teki kanal işlemleri hakkında bilgi edinin. Kanallar, işlemler arası iletişim için bir yol sağlar. İki tür kanal vardır: anonim kanallar ve adlandırılmış kanallar."
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 35a3910bbab1b34f085a55524be0b18b3fa81958
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768891"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="9b400-105">.NET 'teki kanal Işlemleri</span><span class="sxs-lookup"><span data-stu-id="9b400-105">Pipe Operations in .NET</span></span>
<span data-ttu-id="9b400-106">Kanallar, işlemler arası iletişim için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b400-106">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="9b400-107">İki tür kanal vardır:</span><span class="sxs-lookup"><span data-stu-id="9b400-107">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="9b400-108">Anonim kanallar.</span><span class="sxs-lookup"><span data-stu-id="9b400-108">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="9b400-109">Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b400-109">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="9b400-110">Anonim kanallar, adlandırılmış kanallara göre daha az ek yük gerektirir, ancak sınırlı hizmetler sunar.</span><span class="sxs-lookup"><span data-stu-id="9b400-110">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="9b400-111">Anonim kanallar tek yönlü ve ağ üzerinden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9b400-111">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="9b400-112">Yalnızca tek bir sunucu örneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="9b400-112">They support only a single server instance.</span></span> <span data-ttu-id="9b400-113">Anonim kanallar, iş parçacıkları arasındaki iletişim için veya kanal tutamaçlarının oluşturulduğu sırada alt işleme kolayca geçirilebileceği üst ve alt işlemler arasında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9b400-113">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="9b400-114">.NET ' te, ve sınıflarını kullanarak anonim kanallar uygulayacağız <xref:System.IO.Pipes.AnonymousPipeServerStream> <xref:System.IO.Pipes.AnonymousPipeClientStream> .</span><span class="sxs-lookup"><span data-stu-id="9b400-114">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="9b400-115">Bkz. [nasıl yapılır: yerel Işlemler arası iletişim Için anonim kanallar kullanma](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="9b400-115">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="9b400-116">Adlandırılmış kanallar.</span><span class="sxs-lookup"><span data-stu-id="9b400-116">Named pipes.</span></span>  
  
     <span data-ttu-id="9b400-117">Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b400-117">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="9b400-118">Adlandırılmış kanallar tek yönlü veya çift yönlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b400-118">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="9b400-119">İleti tabanlı iletişimi destekler ve aynı kanal adını kullanarak birden fazla istemcinin sunucu işlemine aynı anda bağlanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9b400-119">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="9b400-120">Adlandırılmış Kanallar, kimliğe bürünme özelliğini de destekler ve bu sayede, uzak sunucularda kendi izinlerini kullanmak üzere bağlantı kurma işlemi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9b400-120">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="9b400-121">.NET ' te, ve sınıflarını kullanarak adlandırılmış kanallar uygularmış olursunuz <xref:System.IO.Pipes.NamedPipeServerStream> <xref:System.IO.Pipes.NamedPipeClientStream> .</span><span class="sxs-lookup"><span data-stu-id="9b400-121">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="9b400-122">Bkz. [nasıl yapılır: ağ Işlem iletişimi Için adlandırılmış kanalları kullanma](how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="9b400-122">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b400-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b400-123">See also</span></span>

- [<span data-ttu-id="9b400-124">Dosya ve akış g/ç</span><span class="sxs-lookup"><span data-stu-id="9b400-124">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="9b400-125">Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="9b400-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="9b400-126">Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="9b400-126">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
