---
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352891"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="6cfd3-102">Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6cfd3-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="6cfd3-103">Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini [Nothing](../../../../visual-basic/language-reference/nothing.md)olarak ayarlayarak kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="6cfd3-104">Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="6cfd3-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="6cfd3-105">Değişkeni atama ifadesinde `Nothing` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="6cfd3-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="6cfd3-106">Robust Programming</span></span>  
 <span data-ttu-id="6cfd3-107">Kodunuz, `Nothing`olarak ayarlanmış bir nesne değişkeninin üyesine erişmeyi denediğinde, bir <xref:System.NullReferenceException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="6cfd3-108">Bir nesne değişkenini sıklıkla `Nothing` olarak ayarlarsanız veya değişken başlatılamıyorsa, üye erişimlerini bir `Try...Catch...Finally` bloğuna eklemek iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6cfd3-109">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6cfd3-109">.NET Framework Security</span></span>  
 <span data-ttu-id="6cfd3-110">Gizli veya hassas veriler içeren nesneler için bir nesne değişkeni kullanırsanız, bu nesnelerden biriyle etkin bir şekilde ilgilenirken değişkeni `Nothing` olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="6cfd3-111">Bu, kötü amaçlı kodun verilere erişme olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfd3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cfd3-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="6cfd3-113">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="6cfd3-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="6cfd3-114">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="6cfd3-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="6cfd3-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="6cfd3-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="6cfd3-116">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="6cfd3-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
