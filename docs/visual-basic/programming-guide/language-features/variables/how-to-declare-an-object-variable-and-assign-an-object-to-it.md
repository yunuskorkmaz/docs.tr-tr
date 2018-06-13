---
title: "Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama"
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 1f38c90f0571b3fc73c4c89812092cdada936d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648882"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="26ac6-102">Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama</span><span class="sxs-lookup"><span data-stu-id="26ac6-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="26ac6-103">Bir değişken bildirme [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) belirterek `As Object` içinde bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="26ac6-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="26ac6-104">Nesne sonra eşittir işareti koyarak bir nesne gibi bir değişkene atayın (`=`) atama deyimi veya başlatma yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="26ac6-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26ac6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="26ac6-105">Example</span></span>  
 <span data-ttu-id="26ac6-106">Aşağıdaki örnek bildiren bir `Object` değişkeni ve geçerli örnek için atar.</span><span class="sxs-lookup"><span data-stu-id="26ac6-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="26ac6-107">Değişkeni bildiriminden bir parçası olarak başlatarak ataması ve bildirimi birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26ac6-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="26ac6-108">Aşağıdaki örnek önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="26ac6-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26ac6-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="26ac6-109">Compiling the Code</span></span>  
 <span data-ttu-id="26ac6-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="26ac6-110">This example requires:</span></span>  
  
-   <span data-ttu-id="26ac6-111">Bir başvuru <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="26ac6-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="26ac6-112">Sınıf, yapı veya modülü yerleştirileceği `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="26ac6-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="26ac6-113">Atama deyimi yerleştirileceği bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="26ac6-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ac6-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26ac6-114">See Also</span></span>  
 [<span data-ttu-id="26ac6-115">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="26ac6-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="26ac6-116">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="26ac6-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="26ac6-117">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="26ac6-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="26ac6-118">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="26ac6-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="26ac6-119">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="26ac6-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="26ac6-120">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="26ac6-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="26ac6-121">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="26ac6-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
