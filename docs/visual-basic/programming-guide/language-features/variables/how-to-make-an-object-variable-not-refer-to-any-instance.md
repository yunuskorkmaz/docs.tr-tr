---
title: 'Nasıl yapılır: Nesne değişken olun Başvurmamasını herhangi bir örneğine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 373d4ae84c44b212ad02b0b4266af75921e40423
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818696"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="011e4-102">Nasıl yapılır: Nesne değişken olun Başvurmamasını herhangi bir örneğine (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="011e4-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="011e4-103">Ayarı bir nesne değişkeninin herhangi bir nesne örneğinden ilişkisini [hiçbir şey](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="011e4-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="011e4-104">Bir nesne değişkeninin herhangi bir nesne örneğinden ilişkisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="011e4-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="011e4-105">Değişken kümesine `Nothing` atama deyiminin içinde.</span><span class="sxs-lookup"><span data-stu-id="011e4-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="011e4-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="011e4-106">Robust Programming</span></span>  
 <span data-ttu-id="011e4-107">Kodunuzu bir üyesi olarak ayarlanan bir nesne değişkeninin erişmeye çalışırsa `Nothing`, <xref:System.NullReferenceException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="011e4-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="011e4-108">Bir nesne değişkeninin ayarlamanız `Nothing` sık veya değişken başlatılmamış Mümkünse, kullanma, içine almanız iyi bir fikir bir `Try...Catch...Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="011e4-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="011e4-109">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="011e4-109">.NET Framework Security</span></span>  
 <span data-ttu-id="011e4-110">Gizli veya hassas veriler içeren nesneleri için bir nesne değişkeninin kullanıyorsanız, değişkeni ayarlayabilirsiniz `Nothing` ne zaman, değil etkin bir şekilde ilgilenme nesneleri biriyle.</span><span class="sxs-lookup"><span data-stu-id="011e4-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="011e4-111">Bu, kötü amaçlı kod verilere erişim elde etme olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="011e4-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="011e4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="011e4-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="011e4-113">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="011e4-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="011e4-114">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="011e4-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="011e4-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="011e4-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="011e4-116">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="011e4-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
