---
title: 'Nasıl yapılır: bir nesne değişkeni bildirme ve ona bir nesne atama'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352899"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="ec099-102">Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama</span><span class="sxs-lookup"><span data-stu-id="ec099-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="ec099-103">Bir [Dim ifadesinde](../../../../visual-basic/language-reference/statements/dim-statement.md)`As Object` belirterek [nesne veri türünde](../../../../visual-basic/language-reference/data-types/object-data-type.md) bir değişken bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec099-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="ec099-104">Bir atama deyimi veya başlatma yan tümcesindeki eşittir işaretinden (`=`) sonra nesneyi yerleştirerek bu tür bir değişkene bir nesne atarsınız.</span><span class="sxs-lookup"><span data-stu-id="ec099-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="ec099-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec099-105">Example</span></span>

<span data-ttu-id="ec099-106">Aşağıdaki örnek bir `Object` değişken bildirir ve geçerli örneği buna atar.</span><span class="sxs-lookup"><span data-stu-id="ec099-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="ec099-107">Bildirimi ve atamayı, bildiriminin parçası olarak değişkeni başlatarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec099-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="ec099-108">Aşağıdaki örnek, önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ec099-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="ec099-109">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="ec099-109">Compiling the Code</span></span>

<span data-ttu-id="ec099-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ec099-110">This example requires:</span></span>

- <span data-ttu-id="ec099-111"><xref:System> ad alanına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="ec099-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="ec099-112">`Dim` deyimin konulacağı bir sınıf, yapı veya modül.</span><span class="sxs-lookup"><span data-stu-id="ec099-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="ec099-113">Atama ekstresini koyabileceğiniz bir yordam.</span><span class="sxs-lookup"><span data-stu-id="ec099-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec099-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec099-114">See also</span></span>

- [<span data-ttu-id="ec099-115">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="ec099-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="ec099-116">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ec099-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ec099-117">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="ec099-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="ec099-118">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ec099-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="ec099-119">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec099-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="ec099-120">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="ec099-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="ec099-121">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec099-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
