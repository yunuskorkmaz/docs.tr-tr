---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic değişkenleri'
title: Değişkenler
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: d00907e451fa09c6e9b6be990a24a4d39b386622
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481720"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="e43fb-103">Visual Basic'de Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e43fb-103">Variables in Visual Basic</span></span>

<span data-ttu-id="e43fb-104">Visual Basic hesaplamalar gerçekleştirirken genellikle değerleri depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e43fb-104">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="e43fb-105">Örneğin, karşılaştırma sonucuna bağlı olarak, birkaç değeri hesaplamak, bunları karşılaştırmak ve bunlar üzerinde farklı işlemler gerçekleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e43fb-105">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="e43fb-106">Değerleri karşılaştırmak istiyorsanız saklamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e43fb-106">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e43fb-107">Kullanım</span><span class="sxs-lookup"><span data-stu-id="e43fb-107">Usage</span></span>  

 <span data-ttu-id="e43fb-108">Visual Basic, çoğu programlama dilinde olduğu gibi, değerleri depolamak için değişkenleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="e43fb-108">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="e43fb-109">Bir *değişken* bir ada (değişkenin içerdiği değere başvurmak için kullandığınız sözcük) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e43fb-109">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="e43fb-110">Bir değişken aynı zamanda bir veri türüne sahiptir (değişkenin depolayabileceği veri türünü belirler).</span><span class="sxs-lookup"><span data-stu-id="e43fb-110">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="e43fb-111">Bir değişken, bir dizi yakından ilgili veri öğesi kümesini depolamak için bir diziyi temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="e43fb-111">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="e43fb-112">Yerel tür çıkarımı, bir veri türünü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e43fb-112">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="e43fb-113">Bunun yerine, derleyici değişkenin türünü başlatma ifadesinin türünden algılar.</span><span class="sxs-lookup"><span data-stu-id="e43fb-113">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="e43fb-114">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](local-type-inference.md) ve [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e43fb-114">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="e43fb-115">Değer atama</span><span class="sxs-lookup"><span data-stu-id="e43fb-115">Assigning Values</span></span>  

 <span data-ttu-id="e43fb-116">Aşağıdaki örnekte gösterildiği gibi hesaplamalar gerçekleştirmek ve sonucu bir değişkene atamak için atama deyimlerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e43fb-116">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="e43fb-117">Bu örnekteki eşittir işareti ( `=` ) eşitlik operatörü değil, atama işleçtir.</span><span class="sxs-lookup"><span data-stu-id="e43fb-117">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="e43fb-118">Değer değişkene atanıyor `applesSold` .</span><span class="sxs-lookup"><span data-stu-id="e43fb-118">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="e43fb-119">Daha fazla bilgi için bkz. [nasıl yapılır: bir değişkene veri taşıma ve çıkış](how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="e43fb-119">For more information, see [How to: Move Data Into and Out of a Variable](how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="e43fb-120">Değişkenler ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="e43fb-120">Variables and Properties</span></span>  

 <span data-ttu-id="e43fb-121">Bir değişken gibi bir *özellik* , erişebileceğiniz bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e43fb-121">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="e43fb-122">Ancak, bir değişkenden daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="e43fb-122">However, it is more complex than a variable.</span></span> <span data-ttu-id="e43fb-123">Bir özellik, değerinin nasıl ayarlanacağını ve alınacağını denetleyen kod bloklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e43fb-123">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="e43fb-124">Daha fazla bilgi için, [Visual Basic Özellikler ve değişkenler arasındaki farklılıklar](../procedures/differences-between-properties-and-variables.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e43fb-124">For more information, see [Differences Between Properties and Variables in Visual Basic](../procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e43fb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e43fb-125">See also</span></span>

- [<span data-ttu-id="e43fb-126">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="e43fb-126">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="e43fb-127">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e43fb-127">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="e43fb-128">Değişkenlerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="e43fb-128">Troubleshooting Variables</span></span>](troubleshooting-variables.md)
- [<span data-ttu-id="e43fb-129">Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma</span><span class="sxs-lookup"><span data-stu-id="e43fb-129">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="e43fb-130">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="e43fb-130">Differences Between Properties and Variables in Visual Basic</span></span>](../procedures/differences-between-properties-and-variables.md)
- [<span data-ttu-id="e43fb-131">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e43fb-131">Local Type Inference</span></span>](local-type-inference.md)
