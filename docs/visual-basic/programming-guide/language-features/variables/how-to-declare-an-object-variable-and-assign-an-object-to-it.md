---
title: "Nasıl yapılır: Visual Basic'te Bir Nesne Değişkeni Bildirme ve bir Nesne Atama"
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410509"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="cd1c7-102">Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama</span><span class="sxs-lookup"><span data-stu-id="cd1c7-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="cd1c7-103">Bir Dim Ifadesinde belirterek [nesne veri türünde](../../../language-reference/data-types/object-data-type.md) bir değişken bildirirsiniz `As Object` [Dim Statement](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd1c7-103">You declare a variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="cd1c7-104">Bir `=` atama deyimi veya başlatma yan tümcesindeki eşittir işaretinden () sonra nesneyi yerleştirerek bu tür bir değişkene bir nesne atarsınız.</span><span class="sxs-lookup"><span data-stu-id="cd1c7-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="cd1c7-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd1c7-105">Example</span></span>

<span data-ttu-id="cd1c7-106">Aşağıdaki örnek bir değişken bildirir `Object` ve geçerli örneği buna atar.</span><span class="sxs-lookup"><span data-stu-id="cd1c7-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="cd1c7-107">Bildirimi ve atamayı, bildiriminin parçası olarak değişkeni başlatarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd1c7-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="cd1c7-108">Aşağıdaki örnek, önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cd1c7-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="cd1c7-109">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="cd1c7-109">Compile the code</span></span>

<span data-ttu-id="cd1c7-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cd1c7-110">This example requires:</span></span>

- <span data-ttu-id="cd1c7-111"><xref:System>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="cd1c7-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="cd1c7-112">İfadeye yerleştirilecek bir sınıf, yapı veya modül `Dim` .</span><span class="sxs-lookup"><span data-stu-id="cd1c7-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="cd1c7-113">Atama ekstresini koyabileceğiniz bir yordam.</span><span class="sxs-lookup"><span data-stu-id="cd1c7-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd1c7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd1c7-114">See also</span></span>

- [<span data-ttu-id="cd1c7-115">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="cd1c7-115">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="cd1c7-116">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="cd1c7-116">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="cd1c7-117">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="cd1c7-117">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="cd1c7-118">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="cd1c7-118">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="cd1c7-119">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="cd1c7-119">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="cd1c7-120">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd1c7-120">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="cd1c7-121">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="cd1c7-121">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
