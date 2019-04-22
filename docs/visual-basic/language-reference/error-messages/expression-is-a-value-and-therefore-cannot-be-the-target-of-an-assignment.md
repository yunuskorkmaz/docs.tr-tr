---
title: İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 3027be6ee4ed3664b81c661b6a086a3604573833
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826139"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="793c6-102">İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz</span><span class="sxs-lookup"><span data-stu-id="793c6-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="793c6-103">Bir deyim, deyim için bir değer atamak çalışır.</span><span class="sxs-lookup"><span data-stu-id="793c6-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="793c6-104">Yalnızca bir yazılabilir değişken, özelliği veya dizi öğesi için çalışma zamanında bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="793c6-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="793c6-105">Aşağıdaki örnek nasıl bu hata oluşabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="793c6-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="793c6-106">Benzer örnekler dizi öğeleri ve özellikleri ile uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="793c6-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="793c6-107">**Dolaylı erişim.**</span><span class="sxs-lookup"><span data-stu-id="793c6-107">**Indirect Access.**</span></span> <span data-ttu-id="793c6-108">Bir değer türü aracılığıyla dolaylı erişim de bu hata oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="793c6-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="793c6-109">Değerini ayarlama girişiminde aşağıdaki kod örneği göz önünde bulundurun <xref:System.Drawing.Point> dolaylı olarak aracılığıyla erişerek <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="793c6-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="793c6-110">Yalnızca geçici bir ayırma için oluşturduğundan önceki örnekteki son deyim başarısız <xref:System.Drawing.Point> yapısı tarafından döndürülen <xref:System.Windows.Forms.Control.Location%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="793c6-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="793c6-111">Bir yapı bir değer türüdür ve ifade çalıştıktan sonra geçici yapısı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="793c6-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="793c6-112">Sorun bildirme ve kullanma için bir değişken çözülür <xref:System.Windows.Forms.Control.Location%2A>, için daha kalıcı bir ayırma oluşturur <xref:System.Drawing.Point> yapısı.</span><span class="sxs-lookup"><span data-stu-id="793c6-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="793c6-113">Aşağıdaki örnek, önceki örnekte bulunan son deyim değiştirebilirsiniz kod gösterir.</span><span class="sxs-lookup"><span data-stu-id="793c6-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="793c6-114">**Hata Kimliği:** BC30068</span><span class="sxs-lookup"><span data-stu-id="793c6-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="793c6-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="793c6-115">To correct this error</span></span>  
  
-   <span data-ttu-id="793c6-116">Deyimi, deyim için bir değer atar, ifade tek yazılabilir değişkeni, özelliği veya dizi öğesi ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="793c6-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="793c6-117">İfade bir değer türü (genellikle bir yapı) aracılığıyla dolaylı erişim yaparsa, değer türü tutacak bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="793c6-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="793c6-118">Uygun yapısını (veya başka bir değer türü) değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="793c6-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="793c6-119">Bir değer atamak üzere bir özelliğe erişmek için bu değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="793c6-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793c6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="793c6-120">See also</span></span>

- [<span data-ttu-id="793c6-121">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="793c6-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="793c6-122">Deyimler</span><span class="sxs-lookup"><span data-stu-id="793c6-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="793c6-123">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="793c6-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
