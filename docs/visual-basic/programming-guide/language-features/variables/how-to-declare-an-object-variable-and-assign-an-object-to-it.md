---
title: "Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4a682c7ae32ace0b1f859d52963342546a83f29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="9aa6d-102">Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama</span><span class="sxs-lookup"><span data-stu-id="9aa6d-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="9aa6d-103">Bir değişken bildirme [nesne veri türü](../../../../visual-basic/language-reference/data-types/object-data-type.md) belirterek `As Object` içinde bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9aa6d-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="9aa6d-104">Nesne sonra eşittir işareti koyarak bir nesne gibi bir değişkene atayın (`=`) atama deyimi veya başlatma yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="9aa6d-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aa6d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9aa6d-105">Example</span></span>  
 <span data-ttu-id="9aa6d-106">Aşağıdaki örnek bildiren bir `Object` değişkeni ve geçerli örnek için atar.</span><span class="sxs-lookup"><span data-stu-id="9aa6d-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="9aa6d-107">Değişkeni bildiriminden bir parçası olarak başlatarak ataması ve bildirimi birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9aa6d-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="9aa6d-108">Aşağıdaki örnek önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9aa6d-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9aa6d-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9aa6d-109">Compiling the Code</span></span>  
 <span data-ttu-id="9aa6d-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9aa6d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="9aa6d-111">Bir başvuru <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9aa6d-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="9aa6d-112">Sınıf, yapı veya modülü yerleştirileceği `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="9aa6d-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="9aa6d-113">Atama deyimi yerleştirileceği bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="9aa6d-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa6d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9aa6d-114">See Also</span></span>  
 [<span data-ttu-id="9aa6d-115">Değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="9aa6d-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="9aa6d-116">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9aa6d-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="9aa6d-117">Nesne değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="9aa6d-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="9aa6d-118">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="9aa6d-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="9aa6d-119">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="9aa6d-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="9aa6d-120">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="9aa6d-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="9aa6d-121">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="9aa6d-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
