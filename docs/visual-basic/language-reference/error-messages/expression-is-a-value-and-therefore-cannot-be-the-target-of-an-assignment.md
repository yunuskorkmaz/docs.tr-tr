---
description: 'Hakkında daha fazla bilgi edinin: BC30068: Expression bir değerdir ve bu nedenle bir atamanın hedefi olamaz'
title: İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 424ce9cb0183153454bc068e9da940948b737c47
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796372"
---
# <a name="bc30068-expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="3a1b7-103">BC30068: Ifade bir değerdir ve bu nedenle bir atamanın hedefi olamaz</span><span class="sxs-lookup"><span data-stu-id="3a1b7-103">BC30068: Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="3a1b7-104">Deyim bir ifadeye değer atamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-104">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="3a1b7-105">Çalışma zamanında yalnızca yazılabilir bir değişkene, özelliğe veya dizi öğesine bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-105">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="3a1b7-106">Aşağıdaki örnekte bu hatanın nasıl gerçekleşebileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-106">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="3a1b7-107">Benzer örnekler Özellikler ve dizi öğelerine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-107">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="3a1b7-108">**Dolaylı erişim.**</span><span class="sxs-lookup"><span data-stu-id="3a1b7-108">**Indirect Access.**</span></span> <span data-ttu-id="3a1b7-109">Bir değer türü üzerinden dolaylı erişim bu hatayı da oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-109">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="3a1b7-110">Aşağıdaki kod örneğini göz önünde bulundurun <xref:System.Drawing.Point> . Bu, değeri dolaylı olarak aracılığıyla uygulamasına erişerek değerini ayarlamaya çalışır <xref:System.Windows.Forms.Control.Location%2A> .</span><span class="sxs-lookup"><span data-stu-id="3a1b7-110">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="3a1b7-111">Önceki örneğin son açıklaması, <xref:System.Drawing.Point> özelliği tarafından döndürülen yapı için yalnızca geçici bir ayırma oluşturduğundan başarısız olur <xref:System.Windows.Forms.Control.Location%2A> .</span><span class="sxs-lookup"><span data-stu-id="3a1b7-111">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="3a1b7-112">Yapı bir değer türüdür ve ifade çalıştıktan sonra geçici yapı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-112">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="3a1b7-113">Bu sorun, için bir değişkeni bildirerek ve kullanılarak çözümlenir ve <xref:System.Windows.Forms.Control.Location%2A> Bu da yapı için daha kalıcı bir ayırma oluşturur <xref:System.Drawing.Point> .</span><span class="sxs-lookup"><span data-stu-id="3a1b7-113">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="3a1b7-114">Aşağıdaki örnek, önceki örnekte yer alan son deyimin yerini alacak kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-114">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="3a1b7-115">**Hata kimliği:** BC30068</span><span class="sxs-lookup"><span data-stu-id="3a1b7-115">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3a1b7-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3a1b7-116">To correct this error</span></span>

- <span data-ttu-id="3a1b7-117">Deyim bir ifadeye değer atadığında, ifadeyi tek bir yazılabilir değişken, özellik veya dizi öğesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-117">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="3a1b7-118">İfade bir değer türü (genellikle bir yapı) üzerinden dolaylı erişim yapıyorsa, değer türünü tutmak için bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-118">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="3a1b7-119">Değişkene uygun yapıyı (veya başka bir değer türünü) atayın.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-119">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="3a1b7-120">Değerini bir değer atamak için özelliğe erişmek üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-120">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a1b7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a1b7-121">See also</span></span>

- [<span data-ttu-id="3a1b7-122">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="3a1b7-122">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="3a1b7-123">Deyimler</span><span class="sxs-lookup"><span data-stu-id="3a1b7-123">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="3a1b7-124">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="3a1b7-124">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
