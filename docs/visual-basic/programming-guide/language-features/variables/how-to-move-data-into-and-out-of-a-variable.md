---
title: 'Nasıl yapılır: Veri taşıma içine ve dışına bir değişken (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 30d1c0ab91724ac556e59b272782513ee8b8067b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818546"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="f4e08-102">Nasıl yapılır: Veri taşıma içine ve dışına bir değişken (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4e08-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="f4e08-103">Bir değer atama deyiminin sol tarafında değişken adını koyarak bir değişkende depolayın.</span><span class="sxs-lookup"><span data-stu-id="f4e08-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="f4e08-104">Bir değişkende veri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="f4e08-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="f4e08-105">Değer bir değişkende depolamak için</span><span class="sxs-lookup"><span data-stu-id="f4e08-105">To store a value in a variable</span></span>  
  
-   <span data-ttu-id="f4e08-106">Değişken adı, atama deyiminin sol tarafında kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4e08-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="f4e08-107">Aşağıdaki örnek, değişkenin değerini ayarlar `alpha`.</span><span class="sxs-lookup"><span data-stu-id="f4e08-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="f4e08-108">Atama ifadesi sağ tarafında oluşturulan değeri değişkeninde depolanır.</span><span class="sxs-lookup"><span data-stu-id="f4e08-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="f4e08-109">Bir değişkenden gelen veri alma</span><span class="sxs-lookup"><span data-stu-id="f4e08-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="f4e08-110">Bir değişkenin değeri, değişken adı bir ifade dahil ederek alın.</span><span class="sxs-lookup"><span data-stu-id="f4e08-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="f4e08-111">Bir değişkenden gelen bir değer almak için</span><span class="sxs-lookup"><span data-stu-id="f4e08-111">To retrieve a value from a variable</span></span>  
  
-   <span data-ttu-id="f4e08-112">Değişken adı bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4e08-112">Use the variable name in an expression.</span></span> <span data-ttu-id="f4e08-113">Bir değişkeni kullanabilirsiniz herhangi bir sabit bir değer veya bir sabit değer dışında bir ifadede bir sabitin değeri tanımlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4e08-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="f4e08-114">veya</span><span class="sxs-lookup"><span data-stu-id="f4e08-114">-or-</span></span>  
  
-   <span data-ttu-id="f4e08-115">Eşit aşağıdaki değişken adını kullanın (`=`) bir atama ifadesinde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="f4e08-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="f4e08-116">Aşağıdaki örnek, değişkenin değerini okur `startValue` ve değişkeninin değeri kullanır `counter` bir ifadede.</span><span class="sxs-lookup"><span data-stu-id="f4e08-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="f4e08-117">Değişkeninin değeri ifade yalnızca bir sabit olur ve ardından değişken veya özellik atama ifadesi sol tarafındaki depolanır katılır.</span><span class="sxs-lookup"><span data-stu-id="f4e08-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e08-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4e08-118">See also</span></span>

- [<span data-ttu-id="f4e08-119">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f4e08-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="f4e08-120">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="f4e08-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="f4e08-121">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f4e08-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
