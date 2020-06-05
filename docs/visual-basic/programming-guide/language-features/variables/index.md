---
title: Değişkenler
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: ff617774d7e93ab4238ebc06617cc03fb6bc675a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410392"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="32c24-102">Visual Basic'de Değişkenler</span><span class="sxs-lookup"><span data-stu-id="32c24-102">Variables in Visual Basic</span></span>
<span data-ttu-id="32c24-103">Visual Basic hesaplamalar gerçekleştirirken genellikle değerleri depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c24-103">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="32c24-104">Örneğin, karşılaştırma sonucuna bağlı olarak, birkaç değeri hesaplamak, bunları karşılaştırmak ve bunlar üzerinde farklı işlemler gerçekleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c24-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="32c24-105">Değerleri karşılaştırmak istiyorsanız saklamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c24-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="32c24-106">Kullanım</span><span class="sxs-lookup"><span data-stu-id="32c24-106">Usage</span></span>  
 <span data-ttu-id="32c24-107">Visual Basic, çoğu programlama dilinde olduğu gibi, değerleri depolamak için değişkenleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="32c24-107">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="32c24-108">Bir *değişken* bir ada (değişkenin içerdiği değere başvurmak için kullandığınız sözcük) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="32c24-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="32c24-109">Bir değişken aynı zamanda bir veri türüne sahiptir (değişkenin depolayabileceği veri türünü belirler).</span><span class="sxs-lookup"><span data-stu-id="32c24-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="32c24-110">Bir değişken, bir dizi yakından ilgili veri öğesi kümesini depolamak için bir diziyi temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="32c24-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="32c24-111">Yerel tür çıkarımı, bir veri türünü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="32c24-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="32c24-112">Bunun yerine, derleyici değişkenin türünü başlatma ifadesinin türünden algılar.</span><span class="sxs-lookup"><span data-stu-id="32c24-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="32c24-113">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](local-type-inference.md) ve [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="32c24-113">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="32c24-114">Değer atama</span><span class="sxs-lookup"><span data-stu-id="32c24-114">Assigning Values</span></span>  
 <span data-ttu-id="32c24-115">Aşağıdaki örnekte gösterildiği gibi hesaplamalar gerçekleştirmek ve sonucu bir değişkene atamak için atama deyimlerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="32c24-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="32c24-116">Bu örnekteki eşittir işareti ( `=` ) eşitlik operatörü değil, atama işleçtir.</span><span class="sxs-lookup"><span data-stu-id="32c24-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="32c24-117">Değer değişkene atanıyor `applesSold` .</span><span class="sxs-lookup"><span data-stu-id="32c24-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="32c24-118">Daha fazla bilgi için bkz. [nasıl yapılır: bir değişkene veri taşıma ve çıkış](how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="32c24-118">For more information, see [How to: Move Data Into and Out of a Variable](how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="32c24-119">Değişkenler ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="32c24-119">Variables and Properties</span></span>  
 <span data-ttu-id="32c24-120">Bir değişken gibi bir *özellik* , erişebileceğiniz bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="32c24-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="32c24-121">Ancak, bir değişkenden daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="32c24-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="32c24-122">Bir özellik, değerinin nasıl ayarlanacağını ve alınacağını denetleyen kod bloklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="32c24-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="32c24-123">Daha fazla bilgi için, [Visual Basic Özellikler ve değişkenler arasındaki farklılıklar](../procedures/differences-between-properties-and-variables.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32c24-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c24-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32c24-124">See also</span></span>

- [<span data-ttu-id="32c24-125">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="32c24-125">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="32c24-126">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="32c24-126">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="32c24-127">Değişkenlerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="32c24-127">Troubleshooting Variables</span></span>](troubleshooting-variables.md)
- [<span data-ttu-id="32c24-128">Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma</span><span class="sxs-lookup"><span data-stu-id="32c24-128">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="32c24-129">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="32c24-129">Differences Between Properties and Variables in Visual Basic</span></span>](../procedures/differences-between-properties-and-variables.md)
- [<span data-ttu-id="32c24-130">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32c24-130">Local Type Inference</span></span>](local-type-inference.md)
