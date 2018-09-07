---
title: .NET Framework'te Kanal İşlemleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdc12091a377a118dc533e5f299fa4833af64baf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081875"
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="1923f-102">.NET Framework'te Kanal İşlemleri</span><span class="sxs-lookup"><span data-stu-id="1923f-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="1923f-103">Kanallar, işlemler arası iletişim için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="1923f-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="1923f-104">Kanallar iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="1923f-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="1923f-105">Anonim kanallar.</span><span class="sxs-lookup"><span data-stu-id="1923f-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="1923f-106">Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1923f-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="1923f-107">Anonim kanallar adlandırılmış kanallardan daha az ek yük gerektirir, ancak sınırlı hizmetleri sunar.</span><span class="sxs-lookup"><span data-stu-id="1923f-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="1923f-108">Anonim Kanallar, tek yönlü ve bir ağ üzerinden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1923f-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="1923f-109">Bunlar, yalnızca tek bir sunucu örneği destekler.</span><span class="sxs-lookup"><span data-stu-id="1923f-109">They support only a single server instance.</span></span> <span data-ttu-id="1923f-110">Üst ve alt işlemlerin oluşturulduğunda burada kanal tanıtıcıları kolayca alt işleme geçirilebilir veya iş parçacığı arasında iletişim için anonim kanalları yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1923f-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="1923f-111">.NET Framework anonim kanalları kullanarak uygulamanız <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="1923f-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="1923f-112">Bkz: [nasıl yapılır: yerel işlemler arası iletişim için anonim kanallar kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="1923f-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="1923f-113">Adlandırılmış Kanallar.</span><span class="sxs-lookup"><span data-stu-id="1923f-113">Named pipes.</span></span>  
  
     <span data-ttu-id="1923f-114">Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1923f-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="1923f-115">Adlandırılmış Kanallar, tek yönlü veya çift yönlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1923f-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="1923f-116">Bunlar, ileti tabanlı iletişim destekler ve birden çok istemci aynı anda aynı kanal adını kullanarak sunucu işlemine bağlanmasına izin.</span><span class="sxs-lookup"><span data-stu-id="1923f-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="1923f-117">Adlandırılmış Kanallar, bağlantı işlemlerinin uzak sunucularda kendi izinlerini kullanmasını sağlayan kimliğe bürünme da destekler.</span><span class="sxs-lookup"><span data-stu-id="1923f-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="1923f-118">.NET Framework'teki adlandırılmış kanallar kullanarak uygulamanız <xref:System.IO.Pipes.NamedPipeServerStream> ve <xref:System.IO.Pipes.NamedPipeClientStream> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="1923f-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="1923f-119">Bkz: [nasıl yapılır: ağ işlemler arası iletişimi için adlandırılmış kanallar kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="1923f-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1923f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1923f-120">See also</span></span>

- [<span data-ttu-id="1923f-121">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="1923f-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="1923f-122">Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="1923f-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
- [<span data-ttu-id="1923f-123">Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="1923f-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
