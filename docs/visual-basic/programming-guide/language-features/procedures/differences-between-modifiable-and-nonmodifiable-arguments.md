---
title: "Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="737a9-102">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="737a9-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="737a9-103">Bir yordam çağrısı, genellikle bir veya daha fazla bağımsız değişken için geçirdiğiniz.</span><span class="sxs-lookup"><span data-stu-id="737a9-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="737a9-104">Her bağımsız bir temel programlama öğeye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="737a9-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="737a9-105">Temel alınan öğeleri ve bağımsız değişkenler kendilerini değiştirilebilir veya değiştirilemez olabilir.</span><span class="sxs-lookup"><span data-stu-id="737a9-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="737a9-106">Değiştirilebilir ve değiştirilemez öğeleri</span><span class="sxs-lookup"><span data-stu-id="737a9-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="737a9-107">Bir programlama öğesi ya da olabilir bir *değiştirilebilir öğesi*, değişti, değeri olabilir veya bir *değiştirilemez öğesi*, oluşturulduktan sonra bir sabit değere sahip.</span><span class="sxs-lookup"><span data-stu-id="737a9-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="737a9-108">Aşağıdaki tabloda, değiştirilebilir ve değiştirilemez programlama öğeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="737a9-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="737a9-109">Değiştirilebilir öğeleri</span><span class="sxs-lookup"><span data-stu-id="737a9-109">Modifiable elements</span></span>|<span data-ttu-id="737a9-110">Değiştirilemez öğeleri</span><span class="sxs-lookup"><span data-stu-id="737a9-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="737a9-111">Salt okunur dışında nesne değişkenleri (yordamların içinde bildirilen), yerel değişkenleri dahil</span><span class="sxs-lookup"><span data-stu-id="737a9-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="737a9-112">Salt okunur değişkenler, alanlar ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="737a9-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="737a9-113">Salt okunur dışında alanları (üye değişkenleri) modülleri, sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="737a9-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="737a9-114">Sabit ve değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="737a9-114">Constants and literals</span></span>|  
|<span data-ttu-id="737a9-115">Salt okunur dışında özellikleri</span><span class="sxs-lookup"><span data-stu-id="737a9-115">Properties, except for read-only</span></span>|<span data-ttu-id="737a9-116">Numaralandırma üyeleri</span><span class="sxs-lookup"><span data-stu-id="737a9-116">Enumeration members</span></span>|  
|<span data-ttu-id="737a9-117">Dizi öğeleri</span><span class="sxs-lookup"><span data-stu-id="737a9-117">Array elements</span></span>|<span data-ttu-id="737a9-118">Deyimler (öğelerini değiştirilebilir olsa bile)</span><span class="sxs-lookup"><span data-stu-id="737a9-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="737a9-119">Değiştirilebilir ve değiştirilemez bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="737a9-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="737a9-120">A *değiştirilebilir bağımsız değişkeni* değiştirilebilir ve temel bir öğesiyle biridir.</span><span class="sxs-lookup"><span data-stu-id="737a9-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="737a9-121">Çağrıyı yapan kod herhangi bir zamanda yeni bir değer depolayabilir ve bağımsız değişken geçirirseniz [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), yordamdaki kod çağıran kodu temel alınan öğe de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="737a9-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="737a9-122">A *değiştirilemez bağımsız değişkeni* değiştirilemez bir temel öğeye sahip ya da geçirilen [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="737a9-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="737a9-123">Değiştirilebilir öğesi olsa bile, yordamı çağıran kodu, temel alınan öğe değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="737a9-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="737a9-124">Bunu değiştirilemez bir öğeyse, çağrıyı yapan kod onu değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="737a9-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="737a9-125">Değişiklik çağıran kodu temel alınan öğe etkilemez ancak bu adlı yordamı değiştirilemez bağımsız değişkeni yerel kopyasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="737a9-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737a9-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="737a9-126">See Also</span></span>  
 [<span data-ttu-id="737a9-127">Yordamları</span><span class="sxs-lookup"><span data-stu-id="737a9-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="737a9-128">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="737a9-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="737a9-129">Nasıl yapılır: bir yordama bağımsız değişkenler geçirme</span><span class="sxs-lookup"><span data-stu-id="737a9-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="737a9-130">Bağımsız değişkenleri değere ve başvuruya göre geçirme</span><span class="sxs-lookup"><span data-stu-id="737a9-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="737a9-131">Değere ve başvuruya göre bağımsız değişken geçirme arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="737a9-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="737a9-132">Nasıl yapılır: bir yordam bağımsız değişkeninin değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="737a9-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="737a9-133">Nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma</span><span class="sxs-lookup"><span data-stu-id="737a9-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="737a9-134">Nasıl yapılır: bağımsız değişkeni değere göre geçirilecek şekilde zorlama</span><span class="sxs-lookup"><span data-stu-id="737a9-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="737a9-135">Bağımsız değişkenleri konuma göre ve ada göre geçirme</span><span class="sxs-lookup"><span data-stu-id="737a9-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="737a9-136">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="737a9-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
