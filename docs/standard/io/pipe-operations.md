---
title: .NET'te Boru İşlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706562"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="664f2-102">.NET'te Boru İşlemleri</span><span class="sxs-lookup"><span data-stu-id="664f2-102">Pipe Operations in .NET</span></span>
<span data-ttu-id="664f2-103">Borular süreçler arası iletişim için bir araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="664f2-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="664f2-104">İki tür boru vardır:</span><span class="sxs-lookup"><span data-stu-id="664f2-104">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="664f2-105">İsimsiz borular.</span><span class="sxs-lookup"><span data-stu-id="664f2-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="664f2-106">Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="664f2-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="664f2-107">Anonim borular, adlandırılmış borulardan daha az ek yükü gerektirir, ancak sınırlı hizmetler sunar.</span><span class="sxs-lookup"><span data-stu-id="664f2-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="664f2-108">Anonim borular tek yönlüve ağ üzerinden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="664f2-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="664f2-109">Yalnızca tek bir sunucu örneğini desteklerler.</span><span class="sxs-lookup"><span data-stu-id="664f2-109">They support only a single server instance.</span></span> <span data-ttu-id="664f2-110">Anonim borular, iş parçacıkları arasındaki iletişim için veya boru tutamaçlarıoluşturulduğunda alt işleme kolayca geçirilebilen üst ve alt işlemler arasında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="664f2-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="664f2-111">.NET'te, <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıfları kullanarak anonim borular uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="664f2-111">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="664f2-112">[Bkz. Nasıl Yapılacağını Görün: Yerel İşlemler Arası İletişim için Anonim Borular Kullanın.](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)</span><span class="sxs-lookup"><span data-stu-id="664f2-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="664f2-113">Adı borular.</span><span class="sxs-lookup"><span data-stu-id="664f2-113">Named pipes.</span></span>  
  
     <span data-ttu-id="664f2-114">Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="664f2-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="664f2-115">Adlandırılmış borular tek yönlü veya çift yönlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="664f2-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="664f2-116">İleti tabanlı iletişimi destekler ve aynı boş ad la sunucu işlemine aynı anda bağlanmak için birden çok istemciye izin verir.</span><span class="sxs-lookup"><span data-stu-id="664f2-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="664f2-117">Adlandırılmış kanallar, bağlantı işlemlerinin uzak sunucularda kendi izinlerini kullanmasını sağlayan kimliğe bürünme işlemlerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="664f2-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="664f2-118">.NET'te, adlandırılmış boruları <xref:System.IO.Pipes.NamedPipeServerStream> <xref:System.IO.Pipes.NamedPipeClientStream> ve sınıfları kullanarak uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="664f2-118">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="664f2-119">[Bkz. Nasıl Kullanılır: Ağ İşlemler Arası İletişim için Adlandırılmış Boruları Kullanın.](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)</span><span class="sxs-lookup"><span data-stu-id="664f2-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="664f2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="664f2-120">See also</span></span>

- [<span data-ttu-id="664f2-121">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="664f2-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="664f2-122">Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="664f2-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="664f2-123">Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="664f2-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
