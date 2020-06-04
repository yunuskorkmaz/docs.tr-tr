---
title: Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 733f92cc2cdaa6e923c57649774ceb64de172c18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403349"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="70626-102">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70626-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="70626-103">Bir yordamı çağırdığınızda, genellikle bir veya daha fazla bağımsız değişken geçirin.</span><span class="sxs-lookup"><span data-stu-id="70626-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="70626-104">Her bağımsız değişken temeldeki bir programlama öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="70626-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="70626-105">Hem temel alınan öğeler hem de bağımsız değişkenler değiştirilebilir ya da değiştirilebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="70626-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="70626-106">Değiştirilebilir ve değiştirilemeyen öğeler</span><span class="sxs-lookup"><span data-stu-id="70626-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="70626-107">Bir programlama öğesi, değeri değişmiş olabilen *değiştirilebilir bir öğe*ya da oluşturulduktan sonra sabit bir değere sahip *değiştirilemeyen bir öğe*olabilir.</span><span class="sxs-lookup"><span data-stu-id="70626-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="70626-108">Aşağıdaki tabloda değiştirilebilir ve değiştirilemeyen programlama öğeleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="70626-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="70626-109">Değiştirilebilir öğeler</span><span class="sxs-lookup"><span data-stu-id="70626-109">Modifiable elements</span></span>|<span data-ttu-id="70626-110">Değiştirilemeyen öğeler</span><span class="sxs-lookup"><span data-stu-id="70626-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="70626-111">Salt okunurdur hariç olmak üzere, nesne değişkenleri dahil olmak üzere yerel değişkenler (yordamlar içinde bildirilmiştir)</span><span class="sxs-lookup"><span data-stu-id="70626-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="70626-112">Salt okuma değişkenleri, alanları ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="70626-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="70626-113">Alanlar (modül, sınıf ve yapıların üye değişkenleri), salt okunurdur hariç</span><span class="sxs-lookup"><span data-stu-id="70626-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="70626-114">Sabitler ve sabit değerler</span><span class="sxs-lookup"><span data-stu-id="70626-114">Constants and literals</span></span>|  
|<span data-ttu-id="70626-115">Özellikler, salt okunurdur hariç</span><span class="sxs-lookup"><span data-stu-id="70626-115">Properties, except for read-only</span></span>|<span data-ttu-id="70626-116">Listeleme üyeleri</span><span class="sxs-lookup"><span data-stu-id="70626-116">Enumeration members</span></span>|  
|<span data-ttu-id="70626-117">Dizi öğeleri</span><span class="sxs-lookup"><span data-stu-id="70626-117">Array elements</span></span>|<span data-ttu-id="70626-118">İfadeler (öğeleri değiştirilebilir olsa bile)</span><span class="sxs-lookup"><span data-stu-id="70626-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="70626-119">Değiştirilebilir ve değiştirilemeyen bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="70626-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="70626-120">*Değiştirilebilir bir bağımsız değişken* değiştirilebilir bir temel öğe.</span><span class="sxs-lookup"><span data-stu-id="70626-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="70626-121">Çağıran kod herhangi bir zamanda yeni bir değer saklayabilir ve [ByRef](../../../language-reference/modifiers/byref.md)bağımsız değişkenini geçirirseniz, yordamdaki kod, çağıran kodda temel alınan öğeyi de değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="70626-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="70626-122">*Değiştirilemeyen bir bağımsız değişken* , değiştirilemeyen temel olmayan bir öğeye sahiptir veya [ByVal](../../../language-reference/modifiers/byval.md)' a geçirilir.</span><span class="sxs-lookup"><span data-stu-id="70626-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="70626-123">Yordam, değiştirilebilir bir öğe olsa bile, çağıran kodda temeldeki öğeyi değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="70626-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="70626-124">Değiştirilemeyen bir öğe ise, çağıran kodun kendisi üzerinde değişiklik yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="70626-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="70626-125">Çağrılan yordam, değiştirilemeyen bir bağımsız değişkenin yerel kopyasını değiştirebilir, ancak bu değişiklik çağıran koddaki temeldeki öğeyi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="70626-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70626-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70626-126">See also</span></span>

- [<span data-ttu-id="70626-127">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="70626-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="70626-128">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="70626-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="70626-129">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="70626-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="70626-130">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="70626-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="70626-131">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="70626-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="70626-132">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="70626-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="70626-133">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="70626-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="70626-134">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="70626-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="70626-135">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="70626-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="70626-136">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="70626-136">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
