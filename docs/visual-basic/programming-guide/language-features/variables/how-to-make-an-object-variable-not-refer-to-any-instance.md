---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004908"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="b3511-102">Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3511-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="b3511-103">Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini [Nothing](../../../../visual-basic/language-reference/nothing.md)olarak ayarlayarak kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3511-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="b3511-104">Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="b3511-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="b3511-105">Atama ifadesinde değişkeni `Nothing` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b3511-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="b3511-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b3511-106">Robust Programming</span></span>  
 <span data-ttu-id="b3511-107">Kodunuz `Nothing` olarak ayarlanmış bir nesne değişkeninin üyesine erişmeyi denediğinde, bir <xref:System.NullReferenceException> oluşur.</span><span class="sxs-lookup"><span data-stu-id="b3511-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="b3511-108">@No__t-0 sıklıkla bir nesne değişkeni ayarlarsanız veya değişken başlatılmamış ise, üye erişimlerini bir `Try...Catch...Finally` bloğuna almanız iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="b3511-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b3511-109">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b3511-109">.NET Framework Security</span></span>  
 <span data-ttu-id="b3511-110">Gizli veya hassas veriler içeren nesneler için bir nesne değişkeni kullanırsanız, bu nesnelerden biriyle etkin bir şekilde ilgilenirken değişkeni `Nothing` olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3511-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="b3511-111">Bu, kötü amaçlı kodun verilere erişme olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="b3511-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3511-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3511-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="b3511-113">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="b3511-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="b3511-114">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="b3511-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="b3511-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="b3511-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="b3511-116">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="b3511-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
