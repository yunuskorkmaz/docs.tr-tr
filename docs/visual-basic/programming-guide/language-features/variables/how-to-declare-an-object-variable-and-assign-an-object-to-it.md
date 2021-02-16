---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir nesne değişkeni bildirme ve buna bir nesne atama Visual Basic'
title: "Nasıl yapılır: Visual Basic'te Bir Nesne Değişkeni Bildirme ve bir Nesne Atama"
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: f79cda4507a3dbf2a6946dee7d909b6d1b10802d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481954"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="e3594-103">Nasıl yapılır: Visual Basic'de Bir Nesne Değişkeni Bildirme ve bir Nesne Atama</span><span class="sxs-lookup"><span data-stu-id="e3594-103">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="e3594-104">Bir Dim Ifadesinde belirterek [nesne veri türünde](../../../language-reference/data-types/object-data-type.md) bir değişken bildirirsiniz `As Object` [](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e3594-104">You declare a variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="e3594-105">Bir `=` atama deyimi veya başlatma yan tümcesindeki eşittir işaretinden () sonra nesneyi yerleştirerek bu tür bir değişkene bir nesne atarsınız.</span><span class="sxs-lookup"><span data-stu-id="e3594-105">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="e3594-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3594-106">Example</span></span>

<span data-ttu-id="e3594-107">Aşağıdaki örnek bir değişken bildirir `Object` ve geçerli örneği buna atar.</span><span class="sxs-lookup"><span data-stu-id="e3594-107">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="e3594-108">Bildirimi ve atamayı, bildiriminin parçası olarak değişkeni başlatarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3594-108">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="e3594-109">Aşağıdaki örnek, önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e3594-109">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="e3594-110">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="e3594-110">Compile the code</span></span>

<span data-ttu-id="e3594-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e3594-111">This example requires:</span></span>

- <span data-ttu-id="e3594-112"><xref:System>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="e3594-112">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="e3594-113">İfadeye yerleştirilecek bir sınıf, yapı veya modül `Dim` .</span><span class="sxs-lookup"><span data-stu-id="e3594-113">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="e3594-114">Atama ekstresini koyabileceğiniz bir yordam.</span><span class="sxs-lookup"><span data-stu-id="e3594-114">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3594-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3594-115">See also</span></span>

- [<span data-ttu-id="e3594-116">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="e3594-116">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="e3594-117">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e3594-117">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="e3594-118">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="e3594-118">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="e3594-119">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e3594-119">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="e3594-120">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="e3594-120">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="e3594-121">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3594-121">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="e3594-122">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="e3594-122">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
