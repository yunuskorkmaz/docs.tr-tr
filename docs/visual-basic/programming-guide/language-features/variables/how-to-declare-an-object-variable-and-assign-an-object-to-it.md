---
title: "Nasıl yapılır: Bir nesne değişkeni bildirme ve Visual Basic'te bir nesne atama"
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: e172d62e5bfadded254d5a5fd25b1dcf2da9634d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663590"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="5c5db-102">Nasıl yapılır: Bir nesne değişkeni bildirme ve Visual Basic'te bir nesne atama</span><span class="sxs-lookup"><span data-stu-id="5c5db-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="5c5db-103">Bir değişken bildirmek [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) belirterek `As Object` içinde bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5c5db-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="5c5db-104">Eşittir işaretinden sonra nesne koyarak bir nesne gibi bir değişkene atayın (`=`) bir atama ifadesi veya başlatma yan.</span><span class="sxs-lookup"><span data-stu-id="5c5db-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5db-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c5db-105">Example</span></span>  
 <span data-ttu-id="5c5db-106">Aşağıdaki örnek bildirir bir `Object` değişkeni ve geçerli örnek için atar.</span><span class="sxs-lookup"><span data-stu-id="5c5db-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="5c5db-107">Bildirim ve atamayı bildiriminin bir parçası bir değişkeni başlatarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c5db-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="5c5db-108">Aşağıdaki örnek önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5c5db-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c5db-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5c5db-109">Compiling the Code</span></span>  
 <span data-ttu-id="5c5db-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5c5db-110">This example requires:</span></span>  
  
- <span data-ttu-id="5c5db-111">Bir başvuru <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5c5db-111">A reference to the <xref:System> namespace.</span></span>  
  
- <span data-ttu-id="5c5db-112">Bir sınıf, yapı veya modül yerleştirileceği `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5c5db-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
- <span data-ttu-id="5c5db-113">Atama ifadesi yerleştirileceği bir yordam.</span><span class="sxs-lookup"><span data-stu-id="5c5db-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5db-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c5db-114">See also</span></span>

- [<span data-ttu-id="5c5db-115">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="5c5db-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="5c5db-116">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="5c5db-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="5c5db-117">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="5c5db-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="5c5db-118">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5c5db-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="5c5db-119">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="5c5db-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="5c5db-120">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="5c5db-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="5c5db-121">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="5c5db-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
