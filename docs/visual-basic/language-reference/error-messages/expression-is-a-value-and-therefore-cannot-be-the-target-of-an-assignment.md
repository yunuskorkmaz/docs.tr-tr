---
title: İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: dd5618bd0533f885a6aef8229b2d8cb1bc34c237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590244"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="8eba7-102">İfade bir değerdir, bu nedenle atama işleminin hedefi olamaz</span><span class="sxs-lookup"><span data-stu-id="8eba7-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="8eba7-103">Bir ifade için bir değer atamak bir deyim çalışır.</span><span class="sxs-lookup"><span data-stu-id="8eba7-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="8eba7-104">Çalışma zamanında yalnızca bir yazılabilir değişkeni, özelliği veya dizi öğesi için bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8eba7-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="8eba7-105">Aşağıdaki örnek, bu hata oluşabilir nasıl gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8eba7-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="8eba7-106">Benzer örnekler, özellikleri ve dizi öğeleri için geçerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="8eba7-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="8eba7-107">**Dolaylı erişim.**</span><span class="sxs-lookup"><span data-stu-id="8eba7-107">**Indirect Access.**</span></span> <span data-ttu-id="8eba7-108">Değer türü aracılığıyla dolaylı erişimi de bu hata oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8eba7-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="8eba7-109">Değerini ayarlamaya çalışır aşağıdaki kod örneğinde, göz önünde bulundurun <xref:System.Drawing.Point> dolaylı olarak üzerinden erişerek <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="8eba7-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="8eba7-110">Yalnızca geçici ayırma için oluşturduğundan önceki örnekte son deyim başarısız <xref:System.Drawing.Point> tarafından döndürülen yapısı <xref:System.Windows.Forms.Control.Location%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8eba7-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="8eba7-111">Değer türü yapısıdır ve ifade çalıştıktan sonra geçici yapısı korunmaz.</span><span class="sxs-lookup"><span data-stu-id="8eba7-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="8eba7-112">Sorun bildirme ve bir değişken için kullanarak çözülene <xref:System.Windows.Forms.Control.Location%2A>, daha fazla kalıcı ayırma için oluşturan <xref:System.Drawing.Point> yapısı.</span><span class="sxs-lookup"><span data-stu-id="8eba7-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="8eba7-113">Aşağıdaki örnek önceki örnekte son deyim değiştirebilirsiniz kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eba7-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="8eba7-114">**Hata Kimliği:** BC30068</span><span class="sxs-lookup"><span data-stu-id="8eba7-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8eba7-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8eba7-115">To correct this error</span></span>  
  
-   <span data-ttu-id="8eba7-116">Deyim bir ifade için bir değer atarsa, ifade tek yazılabilir değişken, özelliği veya dizi öğesi ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8eba7-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="8eba7-117">Deyim bir değer türü (genellikle bir yapı) aracılığıyla dolaylı erişim yaparsa, değer türü tutmak için bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8eba7-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="8eba7-118">Uygun yapısı (veya başka bir değer türü) değişkenine atayın.</span><span class="sxs-lookup"><span data-stu-id="8eba7-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="8eba7-119">Bir değer atamak üzere bir özelliğe erişmek için değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="8eba7-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eba7-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8eba7-120">See Also</span></span>  
 [<span data-ttu-id="8eba7-121">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="8eba7-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="8eba7-122">Deyimler</span><span class="sxs-lookup"><span data-stu-id="8eba7-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="8eba7-123">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="8eba7-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
