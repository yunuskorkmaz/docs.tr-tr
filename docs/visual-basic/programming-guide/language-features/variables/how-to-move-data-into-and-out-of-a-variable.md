---
title: 'Nasıl yapılır: Verileri bir değişkene Içine ve dışına taşıma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: df55f122c4ea029a383196f8d9684295ac8926aa
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631117"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="485f8-102">Nasıl yapılır: Verileri bir değişkene Içine ve dışına taşıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="485f8-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="485f8-103">Değişken adını atama ifadesinin sol tarafına koyarak bir değişkende bir değer depolursunuz.</span><span class="sxs-lookup"><span data-stu-id="485f8-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="485f8-104">Verileri bir değişkene koyma</span><span class="sxs-lookup"><span data-stu-id="485f8-104">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="485f8-105">Bir değişkende bir değeri depolamak için</span><span class="sxs-lookup"><span data-stu-id="485f8-105">To store a value in a variable</span></span>

- <span data-ttu-id="485f8-106">Atama ifadesinin sol tarafındaki değişken adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="485f8-106">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="485f8-107">Aşağıdaki örnek, değişkenin `alpha`değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="485f8-107">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="485f8-108">Atama ifadesinin sağ tarafında oluşturulan değer değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="485f8-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="485f8-109">Bir değişkenden veri alma</span><span class="sxs-lookup"><span data-stu-id="485f8-109">Getting Data from a Variable</span></span>

<span data-ttu-id="485f8-110">Değişkenin değerini bir ifadeye değişken adını ekleyerek alırsınız.</span><span class="sxs-lookup"><span data-stu-id="485f8-110">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="485f8-111">Bir değişkenden değer almak için</span><span class="sxs-lookup"><span data-stu-id="485f8-111">To retrieve a value from a variable</span></span>

- <span data-ttu-id="485f8-112">Bir ifadede değişken adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="485f8-112">Use the variable name in an expression.</span></span> <span data-ttu-id="485f8-113">Bir sabiti, bir sabit veya sabit değer, bir sabit değeri tanımlayan bir ifade dışında herhangi bir yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="485f8-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="485f8-114">\-veya</span><span class="sxs-lookup"><span data-stu-id="485f8-114">\-or-</span></span>

- <span data-ttu-id="485f8-115">Atama deyimindeki eşittir (`=`) işaretinden sonraki değişken adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="485f8-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="485f8-116">Aşağıdaki örnek, değişkenin `startValue` değerini okur ve sonra değişkenin `counter` değerini bir ifadede kullanır.</span><span class="sxs-lookup"><span data-stu-id="485f8-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="485f8-117">Değişkenin değeri yalnızca bir sabit olarak ifade edilir ve sonra atama deyiminin sol tarafındaki değişken veya özellikte saklanır.</span><span class="sxs-lookup"><span data-stu-id="485f8-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="485f8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="485f8-118">See also</span></span>

- [<span data-ttu-id="485f8-119">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="485f8-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="485f8-120">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="485f8-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="485f8-121">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="485f8-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
