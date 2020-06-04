---
title: İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 9e4dbaf2f2800454c673cd58ddec4cf0f6e5c6b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409515"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="1b4bf-102">İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz</span><span class="sxs-lookup"><span data-stu-id="1b4bf-102">Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="1b4bf-103">Deyim bir ifadeye değer atamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="1b4bf-104">Çalışma zamanında yalnızca yazılabilir bir değişkene, özelliğe veya dizi öğesine bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="1b4bf-105">Aşağıdaki örnekte bu hatanın nasıl gerçekleşebileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-105">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="1b4bf-106">Benzer örnekler Özellikler ve dizi öğelerine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-106">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="1b4bf-107">**Dolaylı erişim.**</span><span class="sxs-lookup"><span data-stu-id="1b4bf-107">**Indirect Access.**</span></span> <span data-ttu-id="1b4bf-108">Bir değer türü üzerinden dolaylı erişim bu hatayı da oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="1b4bf-109">Aşağıdaki kod örneğini göz önünde bulundurun <xref:System.Drawing.Point> . Bu, değeri dolaylı olarak aracılığıyla uygulamasına erişerek değerini ayarlamaya çalışır <xref:System.Windows.Forms.Control.Location%2A> .</span><span class="sxs-lookup"><span data-stu-id="1b4bf-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="1b4bf-110">Önceki örneğin son açıklaması, <xref:System.Drawing.Point> özelliği tarafından döndürülen yapı için yalnızca geçici bir ayırma oluşturduğundan başarısız olur <xref:System.Windows.Forms.Control.Location%2A> .</span><span class="sxs-lookup"><span data-stu-id="1b4bf-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="1b4bf-111">Yapı bir değer türüdür ve ifade çalıştıktan sonra geçici yapı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="1b4bf-112">Bu sorun, için bir değişkeni bildirerek ve kullanılarak çözümlenir ve <xref:System.Windows.Forms.Control.Location%2A> Bu da yapı için daha kalıcı bir ayırma oluşturur <xref:System.Drawing.Point> .</span><span class="sxs-lookup"><span data-stu-id="1b4bf-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="1b4bf-113">Aşağıdaki örnek, önceki örnekte yer alan son deyimin yerini alacak kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-113">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="1b4bf-114">**Hata kimliği:** BC30068</span><span class="sxs-lookup"><span data-stu-id="1b4bf-114">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1b4bf-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1b4bf-115">To correct this error</span></span>

- <span data-ttu-id="1b4bf-116">Deyim bir ifadeye değer atadığında, ifadeyi tek bir yazılabilir değişken, özellik veya dizi öğesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="1b4bf-117">İfade bir değer türü (genellikle bir yapı) üzerinden dolaylı erişim yapıyorsa, değer türünü tutmak için bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="1b4bf-118">Değişkene uygun yapıyı (veya başka bir değer türünü) atayın.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-118">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="1b4bf-119">Değerini bir değer atamak için özelliğe erişmek üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-119">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b4bf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b4bf-120">See also</span></span>

- [<span data-ttu-id="1b4bf-121">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="1b4bf-121">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="1b4bf-122">Deyimler</span><span class="sxs-lookup"><span data-stu-id="1b4bf-122">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="1b4bf-123">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="1b4bf-123">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
