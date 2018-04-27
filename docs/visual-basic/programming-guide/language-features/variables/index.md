---
title: Visual Basic'de Değişkenler
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e4397fb90e4fa5a3e68390137b84a375cf35956
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="e6c2c-102">Visual Basic'de Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e6c2c-102">Variables in Visual Basic</span></span>
<span data-ttu-id="e6c2c-103">Genellikle, Visual Basic ile hesaplamalar gerçekleştirdiğinizde değerlerini depolamak sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-103">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="e6c2c-104">Örneğin, birkaç değerleri hesaplamak, bunları karşılaştırın ve üzerlerinde, karşılaştırma sonucuna bağlı olarak farklı işlemler gerçekleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="e6c2c-105">Bunları karşılaştırma yapmak isterseniz değerleri tutmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e6c2c-106">Kullanım</span><span class="sxs-lookup"><span data-stu-id="e6c2c-106">Usage</span></span>  
 <span data-ttu-id="e6c2c-107">Visual Basic, yalnızca çoğu programlama dilleri gibi değişkenleri değerlerini depolamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-107">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="e6c2c-108">A *değişkeni* (değişkenini içeren değere başvurmak için kullanacağınız word) olan bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="e6c2c-109">Bir değişken de (hangi değişkeni depolayabilir veri türünü belirler) bir veri türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="e6c2c-110">Dizini oluşturulmuş bir yakından ilgili veri öğeleri kümesi depolamak varsa bir değişken dizisini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="e6c2c-111">Yerel türü çıkarımı açıkça bir veri türü bildirmeden değişkenleri bildirin sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="e6c2c-112">Bunun yerine, derleyici başlatma ifade türü değişkeninden türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="e6c2c-113">Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) ve [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e6c2c-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="e6c2c-114">Değerler atama</span><span class="sxs-lookup"><span data-stu-id="e6c2c-114">Assigning Values</span></span>  
 <span data-ttu-id="e6c2c-115">Atama deyimleri sonucu aşağıdaki örnekte gösterildiği gibi bir değişkene atayın ve hesaplamalar gerçekleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="e6c2c-116">Eşittir işaretinden (`=`) bir eşitlik işleci bir atama işleci Bu örnekte dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="e6c2c-117">Değişkenine atanan değeri `applesSold`.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="e6c2c-118">Daha fazla bilgi için bkz: [nasıl yapılır: veri içine taşıyın ve bir değişkeni dışı](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="e6c2c-118">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="e6c2c-119">Değişkenleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="e6c2c-119">Variables and Properties</span></span>  
 <span data-ttu-id="e6c2c-120">Gibi bir değişken bir *özelliği* erişebileceğiniz bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="e6c2c-121">Ancak, bir değişken karmaşık olur.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="e6c2c-122">Bir özellik ayarlama ve değerini almak nasıl denetim kod blokları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="e6c2c-123">Daha fazla bilgi için bkz: [özellikleri arasındaki farklar ve Visual Basic değişken](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="e6c2c-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c2c-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6c2c-124">See Also</span></span>  
 [<span data-ttu-id="e6c2c-125">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="e6c2c-125">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="e6c2c-126">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e6c2c-126">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="e6c2c-127">Değişkenlerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="e6c2c-127">Troubleshooting Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [<span data-ttu-id="e6c2c-128">Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma</span><span class="sxs-lookup"><span data-stu-id="e6c2c-128">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [<span data-ttu-id="e6c2c-129">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="e6c2c-129">Differences Between Properties and Variables in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [<span data-ttu-id="e6c2c-130">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="e6c2c-130">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
