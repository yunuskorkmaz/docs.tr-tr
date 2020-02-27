---
title: 'Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: ea4aee60d090a56eb0cf3f2a81c1b05c04806d4b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628000"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="31fb2-102">Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="31fb2-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="31fb2-103">Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="31fb2-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="31fb2-104">Adlandırılmış kanallardan daha az işlevsellik sağlarlar, ancak daha az yük gerektirirler.</span><span class="sxs-lookup"><span data-stu-id="31fb2-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="31fb2-105">Yerel bir bilgisayarda işlemler arası iletişimi kolaylaştırmak için anonim kanalları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31fb2-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="31fb2-106">Bir ağ üzerinden iletişim için anonim kanalları kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="31fb2-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="31fb2-107">Anonim kanalları uygulamak için, <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıflarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="31fb2-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31fb2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="31fb2-108">Example</span></span>  
 <span data-ttu-id="31fb2-109">Aşağıdaki örnek, bir ana işlemden alt işleme anonim kanalları kullanarak bir dize göndermenin yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31fb2-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="31fb2-110">Bu örnek, <xref:System.IO.Pipes.AnonymousPipeServerStream>'in bir <xref:System.IO.Pipes.PipeDirection> değeriyle birlikte ana işlemde bir <xref:System.IO.Pipes.PipeDirection.Out> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31fb2-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="31fb2-111">Daha sonra ana işlem, bir <xref:System.IO.Pipes.AnonymousPipeClientStream> nesnesi oluşturmak için bir istemci işleyicisi kullanarak bir alt işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31fb2-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="31fb2-112">Alt işlem, <xref:System.IO.Pipes.PipeDirection>'in bir <xref:System.IO.Pipes.PipeDirection.In> değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="31fb2-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="31fb2-113">Ardından ana işlem, alt işleme kullanıcı tarafından sağlanan bir dize gönderir.</span><span class="sxs-lookup"><span data-stu-id="31fb2-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="31fb2-114">Dize, alt işlemdeki konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="31fb2-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="31fb2-115">Aşağıdaki örnek sunucu işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="31fb2-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="31fb2-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="31fb2-116">Example</span></span>  
 <span data-ttu-id="31fb2-117">Aşağıdaki örnek istemci işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="31fb2-117">The following example shows the client process.</span></span> <span data-ttu-id="31fb2-118">Sunucu işlemi istemci işlemini başlatır ve bu işleme bir istemci işleyicisi verir.</span><span class="sxs-lookup"><span data-stu-id="31fb2-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="31fb2-119">İstemci kodundan oluşturulan yürütülebilir dosya `pipeClient.exe` olarak adlandırılmalıdır ve sunucu işlemi çalıştırılmadan önce sunucu yürütülebilir dosyası olarak aynı dizine kopyalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31fb2-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="31fb2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31fb2-120">See also</span></span>

- [<span data-ttu-id="31fb2-121">Kanallar</span><span class="sxs-lookup"><span data-stu-id="31fb2-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="31fb2-122">Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma</span><span class="sxs-lookup"><span data-stu-id="31fb2-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
