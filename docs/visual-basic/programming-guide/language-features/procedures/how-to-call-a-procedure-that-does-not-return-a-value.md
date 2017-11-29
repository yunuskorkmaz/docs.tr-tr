---
title: "Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbea50132d1110b38bf9b01397795a2cd51f86d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="31347-102">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31347-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="31347-103">A `Sub` yordamı çağıran kodu için bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="31347-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="31347-104">Siz açıkça tek başına bir arama deyimiyle çağrısından.</span><span class="sxs-lookup"><span data-stu-id="31347-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="31347-105">Bu deyim içinde adı kullanılarak çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="31347-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="31347-106">Bir alt yordam çağrısı için</span><span class="sxs-lookup"><span data-stu-id="31347-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="31347-107">Adını belirtin `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="31347-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="31347-108">Bağımsız değişken listesi kapsamak için parantez yordamı adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="31347-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="31347-109">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31347-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="31347-110">Ancak, parantez kullanarak kodunuzu okumak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="31347-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="31347-111">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="31347-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="31347-112">Bağımsız değişkenleri aynı sırada sağladığınız emin olun, `Sub` yordamı ilgili parametreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31347-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="31347-113">Aşağıdaki örnek çağrıları [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> bir uygulama penceresi etkinleştirmek için işlevi.</span><span class="sxs-lookup"><span data-stu-id="31347-113">The following example calls the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="31347-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>pencere başlığı tek bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="31347-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="31347-115">Çağrıyı yapan kod için bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="31347-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="31347-116">Not Defteri işlemi çalışmıyor, örnek döndürürse bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="31347-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="31347-117">`Shell` Yordam varsayar uygulamalardır belirtilen yollar.</span><span class="sxs-lookup"><span data-stu-id="31347-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="31347-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31347-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="31347-119">Yordamları</span><span class="sxs-lookup"><span data-stu-id="31347-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="31347-120">Alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="31347-120">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="31347-121">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="31347-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="31347-122">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="31347-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="31347-123">Nasıl yapılır: bir yordam oluşturma</span><span class="sxs-lookup"><span data-stu-id="31347-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="31347-124">Nasıl yapılır: değer döndüren bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="31347-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="31347-125">Nasıl yapılır: Visual Basic'te bir olay işleyicisi çağırma</span><span class="sxs-lookup"><span data-stu-id="31347-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
