---
title: 'Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 9903a0357d1d8ceade21b590fd54c8cab517f134
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174751"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="38d49-102">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="38d49-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="38d49-103">İzleme için en sık kullanılan yöntemler dinleyicilere çıktı yazma yöntemleridir: **Write** **, WriteIf**, **WriteLine**, **WriteLineIf**, Assert , **ve** **Fail**.</span><span class="sxs-lookup"><span data-stu-id="38d49-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="38d49-104">Bu yöntemler iki kategoriye ayrılabilir: **Yazma**, **WriteLine**, ve **Fail** tüm koşulsuz çıkış yontmak, oysa **WriteIf**, **WriteLineIf**, ve Test bir Boolean durum **assert** ve yazma veya durumun değerine göre yazmayın.</span><span class="sxs-lookup"><span data-stu-id="38d49-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="38d49-105">**WriteIf** ve **WriteLineIf** koşul ise `true`çıktı yayıyorum ve koşul ise `false` **Assert** çıktı yayır.</span><span class="sxs-lookup"><span data-stu-id="38d49-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="38d49-106">İzleme ve hata ayıklama stratejinizi tasarlarken, çıktının nasıl görünmesini istediğinizi düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="38d49-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="38d49-107">İlişkisiz bilgilerle dolu birden çok **Yazma** deyimleri, okunması zor bir günlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38d49-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="38d49-108">Diğer taraftan, ilgili ifadeleri ayrı satırlara koymak için **WriteLine'ı** kullanmak, hangi bilgilerin birbirine ait olduğunu ayırt etmeyi zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="38d49-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="38d49-109">Genel olarak, tek bir bilgilendirici ileti oluşturmak için birden çok kaynaktan gelen bilgileri birleştirmek istediğinizde birden çok **Yazma** deyimi kullanın ve tek bir tam ileti oluşturmak istediğinizde **WriteLine** deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="38d49-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="38d49-110">Tam bir satır yazmak için</span><span class="sxs-lookup"><span data-stu-id="38d49-110">To write a complete line</span></span>  
  
1. <span data-ttu-id="38d49-111">Arama <xref:System.Diagnostics.Trace.WriteLine%2A> veya <xref:System.Diagnostics.Trace.WriteLineIf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38d49-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="38d49-112">Bir satır geri dönüşü iletinin sonuna eklenir, bu yöntem döndürür, böylece sonraki ileti **Write**, **WriteIf**, WriteLine , veya **WriteLineIf**tarafından döndürülür aşağıdaki satırda başlar: **WriteLineIf**</span><span class="sxs-lookup"><span data-stu-id="38d49-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="38d49-113">Kısmi satır yazmak için</span><span class="sxs-lookup"><span data-stu-id="38d49-113">To write a partial line</span></span>  
  
1. <span data-ttu-id="38d49-114">Arama <xref:System.Diagnostics.Trace.Write%2A> veya <xref:System.Diagnostics.Trace.WriteIf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38d49-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="38d49-115">Write , **WriteIf**, **WriteLine** **WriteLine**, veya **WriteLineIf** tarafından söndürülen bir sonraki ileti, **Writeif** **deyimi** tarafından söndürülen iletiyle aynı satırda başlar:</span><span class="sxs-lookup"><span data-stu-id="38d49-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="38d49-116">Bir yöntemi yürütmeden önce veya sonra belirli koşulların mevcut olduğunu doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="38d49-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="38d49-117"><xref:System.Diagnostics.Trace.Assert%2A> Yöntemi ara.</span><span class="sxs-lookup"><span data-stu-id="38d49-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="38d49-118">Hem izleme hem de hata ayıklama ile **Assert'ı** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38d49-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="38d49-119">Bu örnek, çağrı yığınını **Dinleyicikoleksiyonundaki** herhangi bir dinleyiciye çıkar.</span><span class="sxs-lookup"><span data-stu-id="38d49-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="38d49-120">Daha fazla bilgi için [Yönetilen Kod'daki İddialar](/visualstudio/debugger/assertions-in-managed-code) ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38d49-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d49-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38d49-121">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="38d49-122">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="38d49-122">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="38d49-123">Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="38d49-123">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="38d49-124">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="38d49-124">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="38d49-125">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="38d49-125">Trace Listeners</span></span>](trace-listeners.md)
