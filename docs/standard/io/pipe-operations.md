---
title: ".NET Framework'te Kanal İşlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68c1ad34952ee4d20dbf56aa8ca437a3f99db751
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="75047-102">.NET Framework'te Kanal İşlemleri</span><span class="sxs-lookup"><span data-stu-id="75047-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="75047-103">Kanallar, işlemler arası iletişim için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="75047-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="75047-104">Kanallar iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="75047-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="75047-105">Anonim kanallar.</span><span class="sxs-lookup"><span data-stu-id="75047-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="75047-106">Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="75047-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="75047-107">Anonim kanallar adlandırılmış kanallar'den daha az ek yük gerektirir ancak sınırlı hizmetleri sunar.</span><span class="sxs-lookup"><span data-stu-id="75047-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="75047-108">Anonim kanallar tek yönlüdür ve bir ağ üzerinden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="75047-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="75047-109">Bunlar yalnızca tek bir sunucu örneği destekler.</span><span class="sxs-lookup"><span data-stu-id="75047-109">They support only a single server instance.</span></span> <span data-ttu-id="75047-110">Anonim Kanallar, iş parçacıkları arasında ya da oluşturulduğunda, burada kanal tanıtıcıları kolayca alt işlem geçirilebilir üst ve alt işlemleri arasındaki iletişim için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="75047-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="75047-111">.NET Framework, anonim kanallar kullanarak uygulama <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="75047-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="75047-112">Bkz: [nasıl yapılır: yerel işlemler arası iletişim için anonim kanallar kullanma](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="75047-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="75047-113">Adlandırılmış Kanallar.</span><span class="sxs-lookup"><span data-stu-id="75047-113">Named pipes.</span></span>  
  
     <span data-ttu-id="75047-114">Adlandırılmış kanallar, bir kanal sunucusu ve bir veya daha fazla kanal istemcisi arasındaki işlemler arası iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="75047-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="75047-115">Adlandırılmış Kanallar tek yönlü veya çift yönlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="75047-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="75047-116">Bunlar ileti tabanlı iletişim destekler ve birden çok istemcilerin aynı kanal adını kullanarak sunucu işlemi aynı anda bağlanmasına olanak sağlamak.</span><span class="sxs-lookup"><span data-stu-id="75047-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="75047-117">Adlandırılmış kanallar da uzak sunucularda kendi izinlerini kullanmak bağlantı işlemleri sağlayan kimliğe bürünme özelliğini destekler.</span><span class="sxs-lookup"><span data-stu-id="75047-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="75047-118">.NET Framework, adlandırılmış kanallar kullanarak uygulama <xref:System.IO.Pipes.NamedPipeServerStream> ve <xref:System.IO.Pipes.NamedPipeClientStream> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="75047-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="75047-119">Bkz: [nasıl yapılır: ağ işlemler arası iletişimi için adlandırılmış kanallar kullanma](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="75047-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75047-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75047-120">See Also</span></span>  
 [<span data-ttu-id="75047-121">Dosya ve akış t-O</span><span class="sxs-lookup"><span data-stu-id="75047-121">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="75047-122">Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="75047-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="75047-123">Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="75047-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
