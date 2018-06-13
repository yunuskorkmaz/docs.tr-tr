---
title: 'Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: cf136f1486645d6e8e4b5856c0b1baf9e99f6c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649054"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="c8bde-102">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8bde-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="c8bde-103">A `Sub` yordamı çağıran kodu için bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="c8bde-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="c8bde-104">Siz açıkça tek başına bir arama deyimiyle çağrısından.</span><span class="sxs-lookup"><span data-stu-id="c8bde-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="c8bde-105">Bu deyim içinde adı kullanılarak çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="c8bde-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="c8bde-106">Bir alt yordam çağrısı için</span><span class="sxs-lookup"><span data-stu-id="c8bde-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="c8bde-107">Adını belirtin `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="c8bde-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="c8bde-108">Bağımsız değişken listesi kapsamak için parantez yordamı adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="c8bde-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="c8bde-109">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8bde-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="c8bde-110">Ancak, parantez kullanarak kodunuzu okumak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c8bde-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="c8bde-111">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c8bde-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="c8bde-112">Bağımsız değişkenleri aynı sırada sağladığınız emin olun, `Sub` yordamı ilgili parametreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c8bde-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="c8bde-113">Aşağıdaki örnek Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> bir uygulama penceresi etkinleştirmek için işlevi.</span><span class="sxs-lookup"><span data-stu-id="c8bde-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="c8bde-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> pencere başlığı tek bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="c8bde-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="c8bde-115">Çağrıyı yapan kod için bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="c8bde-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="c8bde-116">Not Defteri işlemi çalışmıyor, örnek döndürürse bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c8bde-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="c8bde-117">`Shell` Yordam varsayar uygulamalardır belirtilen yollar.</span><span class="sxs-lookup"><span data-stu-id="c8bde-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c8bde-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8bde-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="c8bde-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c8bde-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="c8bde-120">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c8bde-120">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="c8bde-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="c8bde-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c8bde-122">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="c8bde-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="c8bde-123">Nasıl yapılır: Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8bde-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="c8bde-124">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="c8bde-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="c8bde-125">Nasıl yapılır: Visual Basic'te bir olay işleyicisi çağırma</span><span class="sxs-lookup"><span data-stu-id="c8bde-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
