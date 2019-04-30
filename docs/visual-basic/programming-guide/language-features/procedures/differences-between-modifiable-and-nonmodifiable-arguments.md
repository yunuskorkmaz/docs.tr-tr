---
title: Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: a880ae8c13eebd5d9d325468098e058f58d3fa71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665955"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="9f278-102">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f278-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="9f278-103">Bir yordamı çağırdığınızda, genellikle bir veya daha fazla bağımsız değişken geçirin.</span><span class="sxs-lookup"><span data-stu-id="9f278-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="9f278-104">Her bir bağımsız değişkenin temel alınan bir programlama öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9f278-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="9f278-105">Temel alınan öğeleri hem bağımsız değiştirilebilir veya değiştirilemez olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f278-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="9f278-106">Öğeler değiştirilebilir ve değiştirilemez</span><span class="sxs-lookup"><span data-stu-id="9f278-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="9f278-107">Bir programlama öğesi olabilir bir *değiştirilebilir öğesi*, değişen değeri olabilir veya *değiştirilemez öğenin*, oluşturulduktan sonra sabit bir değere sahip.</span><span class="sxs-lookup"><span data-stu-id="9f278-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="9f278-108">Aşağıdaki tabloda, değiştirilebilir ve değiştirilemez programlama öğelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9f278-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="9f278-109">Değiştirilebilir öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f278-109">Modifiable elements</span></span>|<span data-ttu-id="9f278-110">Değiştirilemez öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f278-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="9f278-111">Salt okunur hariç nesne değişkenleri (yordamların içinde bildirilen), yerel değişkenleri de dahil olmak üzere</span><span class="sxs-lookup"><span data-stu-id="9f278-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="9f278-112">Salt okunur değişkenler, alanlar ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="9f278-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="9f278-113">Salt okunur dışında alanlar (üye değişkenleri) modülleri, sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="9f278-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="9f278-114">Sabit ve değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="9f278-114">Constants and literals</span></span>|  
|<span data-ttu-id="9f278-115">Salt okunur dışındaki özellikleri</span><span class="sxs-lookup"><span data-stu-id="9f278-115">Properties, except for read-only</span></span>|<span data-ttu-id="9f278-116">Numaralandırma üyeleri</span><span class="sxs-lookup"><span data-stu-id="9f278-116">Enumeration members</span></span>|  
|<span data-ttu-id="9f278-117">Dizi öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f278-117">Array elements</span></span>|<span data-ttu-id="9f278-118">İfadeler (öğeleri değiştirilebilir olsa bile)</span><span class="sxs-lookup"><span data-stu-id="9f278-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="9f278-119">Değiştirilebilir ve değiştirilemez bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="9f278-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="9f278-120">A *değiştirilebilir bağımsız değişken* değiştirilebilir bir temel alınan öğe biridir.</span><span class="sxs-lookup"><span data-stu-id="9f278-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="9f278-121">Çağıran kod, herhangi bir zamanda yeni bir değer depolayabilir ve bağımsız değişken geçirirseniz [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), yordamda kod çağıran koddaki temel alınan öğe de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f278-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="9f278-122">A *değiştirilemez bağımsız değişken* değiştirilemez bir alt öğeye sahip ya da geçirilir [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="9f278-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="9f278-123">Değiştirilebilir bir öğe olsa bile, yordamı çağıran kod, temel alınan öğe değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f278-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="9f278-124">Çağıran kod, değiştirilemez bir öğeyse, değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f278-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="9f278-125">Değişiklik, temel alınan öğe çağıran koddaki etkilemez ancak bu, çağrılan yordam değiştirilemez bir bağımsız değişken yerel kopyasına değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f278-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f278-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f278-126">See also</span></span>

- [<span data-ttu-id="9f278-127">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9f278-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9f278-128">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9f278-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9f278-129">Nasıl yapılır: Bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="9f278-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="9f278-130">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9f278-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="9f278-131">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="9f278-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="9f278-132">Nasıl yapılır: Bir yordam bağımsız değişkeninin değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="9f278-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="9f278-133">Nasıl yapılır: Bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma</span><span class="sxs-lookup"><span data-stu-id="9f278-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="9f278-134">Nasıl yapılır: Bağımsız değişkeni değere göre geçirilecek şekilde zorlama</span><span class="sxs-lookup"><span data-stu-id="9f278-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="9f278-135">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="9f278-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="9f278-136">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="9f278-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
