---
title: Mid deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: a653e63ded04616b6b0c6bdfb26a0a673d9299fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209361"
---
# <a name="mid-statement"></a><span data-ttu-id="556fa-102">Mid Deyimi</span><span class="sxs-lookup"><span data-stu-id="556fa-102">Mid Statement</span></span>
<span data-ttu-id="556fa-103">Belirtilen sayıda karakter yerini alan bir `String` başka bir dizeden karakterlerle değişken.</span><span class="sxs-lookup"><span data-stu-id="556fa-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="556fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="556fa-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="556fa-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="556fa-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="556fa-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="556fa-106">Required.</span></span> <span data-ttu-id="556fa-107">Adını `String` değiştirmek için değişken.</span><span class="sxs-lookup"><span data-stu-id="556fa-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="556fa-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="556fa-108">Required.</span></span> <span data-ttu-id="556fa-109">`Integer` ifade.</span><span class="sxs-lookup"><span data-stu-id="556fa-109">`Integer` expression.</span></span> <span data-ttu-id="556fa-110">Karakter konumunda `Target` burada metin değiştirmesinin.</span><span class="sxs-lookup"><span data-stu-id="556fa-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="556fa-111">`Start` bir tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="556fa-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="556fa-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="556fa-112">Optional.</span></span> <span data-ttu-id="556fa-113">`Integer` ifade.</span><span class="sxs-lookup"><span data-stu-id="556fa-113">`Integer` expression.</span></span> <span data-ttu-id="556fa-114">Değiştirilecek karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="556fa-114">Number of characters to replace.</span></span> <span data-ttu-id="556fa-115">Atlanırsa, tüm `String` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="556fa-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="556fa-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="556fa-116">Required.</span></span> <span data-ttu-id="556fa-117">`String` bölümünü değiştirir ifade `Target`.</span><span class="sxs-lookup"><span data-stu-id="556fa-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="556fa-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="556fa-118">Exceptions</span></span>  
  
|<span data-ttu-id="556fa-119">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="556fa-119">Exception type</span></span>|<span data-ttu-id="556fa-120">Koşul</span><span class="sxs-lookup"><span data-stu-id="556fa-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="556fa-121">`Start` < = 0 veya `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="556fa-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="556fa-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="556fa-122">Remarks</span></span>  
 <span data-ttu-id="556fa-123">Değiştirilen karakter sayısını her zaman eşit veya karakter sayısı küçüktür `Target`.</span><span class="sxs-lookup"><span data-stu-id="556fa-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="556fa-124">Visual Basic sahip bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işlevi ve bir `Mid` deyimi.</span><span class="sxs-lookup"><span data-stu-id="556fa-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="556fa-125">Bu öğelerden hem de çalışan bir belirtilen bir dizedeki karakter sayısına ancak `Mid` işlevi çalışırken karakterleri döndürür `Mid` deyimi karakterleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="556fa-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="556fa-126">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="556fa-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="556fa-127">`MidB` Visual Basic'in önceki sürümlerindeki deyiminin karakter yerine bayt bir alt dizeyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="556fa-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="556fa-128">Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="556fa-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="556fa-129">Tüm Visual Basic dizeleri Unicode biçimindedir ve `MidB` artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="556fa-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="556fa-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="556fa-130">Example</span></span>  
 <span data-ttu-id="556fa-131">Bu örnekte `Mid` deyimi başka bir dizeden karakterlerle belirtilen sayıda karakteri bir dize değişkeniyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="556fa-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="556fa-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="556fa-132">Requirements</span></span>  
 <span data-ttu-id="556fa-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="556fa-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="556fa-134">**Modül:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="556fa-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="556fa-135">**Derleme:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="556fa-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556fa-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="556fa-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="556fa-137">Dizeler</span><span class="sxs-lookup"><span data-stu-id="556fa-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="556fa-138">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="556fa-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
