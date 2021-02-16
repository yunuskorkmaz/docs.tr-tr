---
description: 'Daha fazla bilgi: değiştirilebilir ve değiştirilemeyen bağımsız değişkenler arasındaki farklar (Visual Basic)'
title: Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 8d83802b4b8830a17412fdef44eabd2e5b8a7f2d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472637"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="5ebae-103">Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ebae-103">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>

<span data-ttu-id="5ebae-104">Bir yordamı çağırdığınızda, genellikle bir veya daha fazla bağımsız değişken geçirin.</span><span class="sxs-lookup"><span data-stu-id="5ebae-104">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="5ebae-105">Her bağımsız değişken temeldeki bir programlama öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5ebae-105">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="5ebae-106">Hem temel alınan öğeler hem de bağımsız değişkenler değiştirilebilir ya da değiştirilebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ebae-106">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="5ebae-107">Değiştirilebilir ve değiştirilemeyen öğeler</span><span class="sxs-lookup"><span data-stu-id="5ebae-107">Modifiable and Nonmodifiable Elements</span></span>  

 <span data-ttu-id="5ebae-108">Bir programlama öğesi, değeri değişmiş olabilen *değiştirilebilir bir öğe* ya da oluşturulduktan sonra sabit bir değere sahip *değiştirilemeyen bir öğe* olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ebae-108">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="5ebae-109">Aşağıdaki tabloda değiştirilebilir ve değiştirilemeyen programlama öğeleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ebae-109">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="5ebae-110">Değiştirilebilir öğeler</span><span class="sxs-lookup"><span data-stu-id="5ebae-110">Modifiable elements</span></span>|<span data-ttu-id="5ebae-111">Değiştirilemeyen öğeler</span><span class="sxs-lookup"><span data-stu-id="5ebae-111">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="5ebae-112">Salt okunurdur hariç olmak üzere, nesne değişkenleri dahil olmak üzere yerel değişkenler (yordamlar içinde bildirilmiştir)</span><span class="sxs-lookup"><span data-stu-id="5ebae-112">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="5ebae-113">Salt okuma değişkenleri, alanları ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="5ebae-113">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="5ebae-114">Alanlar (modül, sınıf ve yapıların üye değişkenleri), salt okunurdur hariç</span><span class="sxs-lookup"><span data-stu-id="5ebae-114">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="5ebae-115">Sabitler ve sabit değerler</span><span class="sxs-lookup"><span data-stu-id="5ebae-115">Constants and literals</span></span>|  
|<span data-ttu-id="5ebae-116">Özellikler, salt okunurdur hariç</span><span class="sxs-lookup"><span data-stu-id="5ebae-116">Properties, except for read-only</span></span>|<span data-ttu-id="5ebae-117">Listeleme üyeleri</span><span class="sxs-lookup"><span data-stu-id="5ebae-117">Enumeration members</span></span>|  
|<span data-ttu-id="5ebae-118">Dizi öğeleri</span><span class="sxs-lookup"><span data-stu-id="5ebae-118">Array elements</span></span>|<span data-ttu-id="5ebae-119">İfadeler (öğeleri değiştirilebilir olsa bile)</span><span class="sxs-lookup"><span data-stu-id="5ebae-119">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="5ebae-120">Değiştirilebilir ve değiştirilemeyen bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="5ebae-120">Modifiable and Nonmodifiable Arguments</span></span>  

 <span data-ttu-id="5ebae-121">*Değiştirilebilir bir bağımsız değişken* değiştirilebilir bir temel öğe.</span><span class="sxs-lookup"><span data-stu-id="5ebae-121">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="5ebae-122">Çağıran kod herhangi bir zamanda yeni bir değer saklayabilir ve [ByRef](../../../language-reference/modifiers/byref.md)bağımsız değişkenini geçirirseniz, yordamdaki kod, çağıran kodda temel alınan öğeyi de değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5ebae-122">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="5ebae-123">*Değiştirilemeyen bir bağımsız değişken* , değiştirilemeyen temel olmayan bir öğeye sahiptir veya [ByVal](../../../language-reference/modifiers/byval.md)' a geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5ebae-123">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="5ebae-124">Yordam, değiştirilebilir bir öğe olsa bile, çağıran kodda temeldeki öğeyi değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="5ebae-124">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="5ebae-125">Değiştirilemeyen bir öğe ise, çağıran kodun kendisi üzerinde değişiklik yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="5ebae-125">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="5ebae-126">Çağrılan yordam, değiştirilemeyen bir bağımsız değişkenin yerel kopyasını değiştirebilir, ancak bu değişiklik çağıran koddaki temeldeki öğeyi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="5ebae-126">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebae-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ebae-127">See also</span></span>

- [<span data-ttu-id="5ebae-128">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5ebae-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="5ebae-129">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="5ebae-129">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5ebae-130">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="5ebae-130">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="5ebae-131">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="5ebae-131">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="5ebae-132">Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="5ebae-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="5ebae-133">Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="5ebae-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="5ebae-134">Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma</span><span class="sxs-lookup"><span data-stu-id="5ebae-134">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="5ebae-135">Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama</span><span class="sxs-lookup"><span data-stu-id="5ebae-135">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="5ebae-136">Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="5ebae-136">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="5ebae-137">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="5ebae-137">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
