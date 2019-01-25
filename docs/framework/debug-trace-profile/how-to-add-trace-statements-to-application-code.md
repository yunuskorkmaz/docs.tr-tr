---
title: 'Nasıl yapılır: Uygulama koduna izleme deyimleri ekleme'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a347919617e495ace19ca12eebc9b9a77f613ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684386"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="0ca2c-102">Nasıl yapılır: Uygulama koduna izleme deyimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="0ca2c-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="0ca2c-103">İzleme için en sık kullanılan yöntemleri çıkış dinleyicileri için yazma yöntemleri şunlardır: **Yazma**, **Writeıf**, **WriteLine**, **Writelineıf**, **Assert**, ve **başarısız**.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="0ca2c-104">Bu yöntemleri iki kategoriye ayrılabilir: **Yazma**, **WriteLine**, ve **başarısız** tüm çıkış koşulsuz, oysa yayma **Writeıf**, **Writelineıf**ve  **Assert** bir Boolean koşulu test yazma ve koşul değerine göre yazma.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="0ca2c-105">**Writeıf** ve **Writelineıf** koşul ise çıktı yayma `true`, ve **Assert** koşul ise, çıktıyı yayar `false`.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="0ca2c-106">İzleme ve hata ayıklama stratejisi tasarlarken, aramak için çıkış biçimini hakkında almalısınız.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="0ca2c-107">Birden çok **yazma** ilgisiz bilgilerle doldurulmuş deyimleri okunması zor bir günlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="0ca2c-108">Öte yandan, kullanarak **WriteLine** ilgili deyimleri koymak için ayrı satırlara, hangi bilgilerin birlikte ait ayırt etmek zor duruma getirebilir.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="0ca2c-109">Genel olarak, birden çok kullanın **yazma** tek bir bilgilendirici ileti oluşturmak ve kullanmak için birden fazla kaynaktan bilgileri birleştirmek istediğinizde deyimleri **WriteLine** oluşturmak istediğinizde deyimi bir tek ve eksiksiz iletisi.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="0ca2c-110">Tam bir satır yazmak için</span><span class="sxs-lookup"><span data-stu-id="0ca2c-110">To write a complete line</span></span>  
  
1.  <span data-ttu-id="0ca2c-111">Arama <xref:System.Diagnostics.Trace.WriteLine%2A> veya <xref:System.Diagnostics.Trace.WriteLineIf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="0ca2c-112">Böylece sonraki iletiyi tarafından döndürülen bir satır başı, bu yöntem tarafından döndürülen ileti sonuna eklenir **yazma**, **Writeıf**, **WriteLine**, veya  **Writelineıf** satırında başlar:</span><span class="sxs-lookup"><span data-stu-id="0ca2c-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
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
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="0ca2c-113">Kısmi bir satır yazmak için</span><span class="sxs-lookup"><span data-stu-id="0ca2c-113">To write a partial line</span></span>  
  
1.  <span data-ttu-id="0ca2c-114">Arama <xref:System.Diagnostics.Trace.Write%2A> veya <xref:System.Diagnostics.Trace.WriteIf%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="0ca2c-115">Sonraki iletiyi bırakırsınız bir **yazma**, **Writeıf**, **WriteLine**, veya **Writelineıf** tarafından put ileti ile aynı satırda başlayacak **yazma** veya **Writeıf** deyimi:</span><span class="sxs-lookup"><span data-stu-id="0ca2c-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="0ca2c-116">Doğrulamak için belirli koşullar önce veya sonra bir yöntem yürütülmeye var</span><span class="sxs-lookup"><span data-stu-id="0ca2c-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1.  <span data-ttu-id="0ca2c-117">Çağrı <xref:System.Diagnostics.Trace.Assert%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0ca2c-118">Kullanabileceğiniz **Assert** izleme ve hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="0ca2c-119">Bu örnek herhangi bir dinleyici için çağrı yığınını çıkarır **dinleyicileri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="0ca2c-120">Daha fazla bilgi için [yönetilen koddaki onaylar](/visualstudio/debugger/assertions-in-managed-code) ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca2c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-121">See also</span></span>
- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0ca2c-122">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="0ca2c-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="0ca2c-123">Nasıl yapılır: Oluşturma, başlatma ve izleme anahtarları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0ca2c-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="0ca2c-124">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="0ca2c-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="0ca2c-125">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="0ca2c-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
