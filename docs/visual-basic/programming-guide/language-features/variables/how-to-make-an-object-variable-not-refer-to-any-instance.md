---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir nesne değişkeninin herhangi bir örneğe başvurmadığından emin olun (Visual Basic)'
title: 'Nasıl yapılır: Bir Nesne Değişkeninin Bir Örneğine Başvurmamasını Sağlama'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 2897720b52e708847fdd139be512e578a7420241
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481876"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="09d55-103">Nasıl yapılır: Bir Nesne Değişkeninin Hiçbir Örneğe Başvurmamasını Sağlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09d55-103">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>

<span data-ttu-id="09d55-104">Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini [Nothing](../../../language-reference/nothing.md)olarak ayarlayarak kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09d55-104">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="09d55-105">Herhangi bir nesne örneğinden bir nesne değişkeninin ilişkisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="09d55-105">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="09d55-106">Değişkenini `Nothing` atama ifadesinde olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="09d55-106">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="09d55-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="09d55-107">Robust Programming</span></span>  

 <span data-ttu-id="09d55-108">Kodunuz, olarak ayarlanmış bir nesne değişkeninin üyesine erişmeye çalışırsa `Nothing` , bir <xref:System.NullReferenceException> gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="09d55-108">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="09d55-109">Bir nesne değişkenini sıklıkla olarak ayarlarsanız `Nothing` veya değişken başlatılmamış ise, üye erişimlerini bir blokta kapsamak iyi bir fikirdir `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="09d55-109">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="09d55-110">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="09d55-110">.NET Framework Security</span></span>  

 <span data-ttu-id="09d55-111">Gizli veya hassas veriler içeren nesneler için bir nesne değişkeni kullanırsanız, `Nothing` bu nesnelerden biriyle etkin bir şekilde ilgilenmediği zaman değişkenini olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09d55-111">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="09d55-112">Bu, kötü amaçlı kodun verilere erişme olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="09d55-112">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09d55-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09d55-113">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="09d55-114">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="09d55-114">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="09d55-115">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="09d55-115">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="09d55-116">Nothing</span><span class="sxs-lookup"><span data-stu-id="09d55-116">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="09d55-117">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="09d55-117">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
