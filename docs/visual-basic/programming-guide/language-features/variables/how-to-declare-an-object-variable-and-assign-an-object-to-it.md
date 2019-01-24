---
title: "Nasıl yapılır: Bir nesne değişkeni bildirme ve Visual Basic'te bir nesne atama"
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 86037499b44d17f2ba83fd6cd0dad83ceb14e6b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730093"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="fb2dc-102">Nasıl yapılır: Bir nesne değişkeni bildirme ve Visual Basic'te bir nesne atama</span><span class="sxs-lookup"><span data-stu-id="fb2dc-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="fb2dc-103">Bir değişken bildirmek [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) belirterek `As Object` içinde bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb2dc-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="fb2dc-104">Eşittir işaretinden sonra nesne koyarak bir nesne gibi bir değişkene atayın (`=`) bir atama ifadesi veya başlatma yan.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb2dc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb2dc-105">Example</span></span>  
 <span data-ttu-id="fb2dc-106">Aşağıdaki örnek bildirir bir `Object` değişkeni ve geçerli örnek için atar.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="fb2dc-107">Bildirim ve atamayı bildiriminin bir parçası bir değişkeni başlatarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="fb2dc-108">Aşağıdaki örnek önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fb2dc-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fb2dc-109">Compiling the Code</span></span>  
 <span data-ttu-id="fb2dc-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fb2dc-110">This example requires:</span></span>  
  
-   <span data-ttu-id="fb2dc-111">Bir başvuru <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="fb2dc-112">Bir sınıf, yapı veya modül yerleştirileceği `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="fb2dc-113">Atama ifadesi yerleştirileceği bir yordam.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2dc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-114">See also</span></span>
- [<span data-ttu-id="fb2dc-115">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="fb2dc-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="fb2dc-116">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="fb2dc-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="fb2dc-117">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="fb2dc-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="fb2dc-118">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="fb2dc-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="fb2dc-119">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="fb2dc-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="fb2dc-120">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="fb2dc-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="fb2dc-121">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="fb2dc-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
