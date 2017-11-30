---
title: "Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f457cc91e6fbfc118e5363d1b0a8e8c2ad800748
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="e764e-102">Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="e764e-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="e764e-103">Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e764e-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="e764e-104">Adlandırılmış kanallardan daha az işlevsellik sağlarlar, ancak daha az yük gerektirirler.</span><span class="sxs-lookup"><span data-stu-id="e764e-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="e764e-105">Yerel bir bilgisayarda işlemler arası iletişimi kolaylaştırmak için anonim kanalları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e764e-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="e764e-106">Bir ağ üzerinden iletişim için anonim kanalları kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e764e-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="e764e-107">Anonim kanalları uygulamak için, <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıflarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e764e-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e764e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e764e-108">Example</span></span>  
 <span data-ttu-id="e764e-109">Aşağıdaki örnek, bir ana işlemden alt işleme anonim kanalları kullanarak bir dize göndermenin yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e764e-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="e764e-110">Bu örnek, <xref:System.IO.Pipes.AnonymousPipeServerStream>'in bir <xref:System.IO.Pipes.PipeDirection> değeriyle birlikte ana işlemde bir <xref:System.IO.Pipes.PipeDirection.Out> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e764e-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="e764e-111">Daha sonra ana işlem, bir <xref:System.IO.Pipes.AnonymousPipeClientStream> nesnesi oluşturmak için bir istemci işleyicisi kullanarak bir alt işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e764e-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="e764e-112">Alt işlem, <xref:System.IO.Pipes.PipeDirection>'in bir <xref:System.IO.Pipes.PipeDirection.In> değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e764e-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="e764e-113">Ardından ana işlem, alt işleme kullanıcı tarafından sağlanan bir dize gönderir.</span><span class="sxs-lookup"><span data-stu-id="e764e-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="e764e-114">Dize, alt işlemdeki konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e764e-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="e764e-115">Aşağıdaki örnek sunucu işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e764e-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="e764e-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="e764e-116">Example</span></span>  
 <span data-ttu-id="e764e-117">Aşağıdaki örnek istemci işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e764e-117">The following example shows the client process.</span></span> <span data-ttu-id="e764e-118">Sunucu işlemi istemci işlemini başlatır ve bu işleme bir istemci işleyicisi verir.</span><span class="sxs-lookup"><span data-stu-id="e764e-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="e764e-119">İstemci kodundan oluşturulan yürütülebilir dosya `pipeClient.exe` olarak adlandırılmalıdır ve sunucu işlemi çalıştırılmadan önce sunucu yürütülebilir dosyası olarak aynı dizine kopyalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e764e-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="e764e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e764e-120">See Also</span></span>  
 [<span data-ttu-id="e764e-121">Kanallar</span><span class="sxs-lookup"><span data-stu-id="e764e-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="e764e-122">Nasıl yapılır: ağ işlemler arası iletişimi için adlandırılmış kanallar kullanma</span><span class="sxs-lookup"><span data-stu-id="e764e-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
