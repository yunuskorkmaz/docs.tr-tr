---
title: Mid açıklaması (Visual Basic)
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
ms.openlocfilehash: ea22af2eb896542bfc329e087101608e08c45107
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581484"
---
# <a name="mid-statement"></a><span data-ttu-id="bf244-102">Mid Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf244-102">Mid Statement</span></span>
<span data-ttu-id="bf244-103">Bir `String` değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterlerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bf244-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf244-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf244-104">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="bf244-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="bf244-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="bf244-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bf244-106">Required.</span></span> <span data-ttu-id="bf244-107">Değiştirilecek `String` değişkeninin adı.</span><span class="sxs-lookup"><span data-stu-id="bf244-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="bf244-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bf244-108">Required.</span></span> <span data-ttu-id="bf244-109">`Integer` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="bf244-109">`Integer` expression.</span></span> <span data-ttu-id="bf244-110">Metnin değiştirme işleminin başladığı `Target` karakter konumu.</span><span class="sxs-lookup"><span data-stu-id="bf244-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="bf244-111">`Start`, tek tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf244-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="bf244-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bf244-112">Optional.</span></span> <span data-ttu-id="bf244-113">`Integer` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="bf244-113">`Integer` expression.</span></span> <span data-ttu-id="bf244-114">Değiştirilecek karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="bf244-114">Number of characters to replace.</span></span> <span data-ttu-id="bf244-115">Atlanırsa, tüm `String` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf244-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="bf244-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="bf244-116">Required.</span></span> <span data-ttu-id="bf244-117">`Target` kısmını değiştiren `String` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="bf244-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="bf244-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="bf244-118">Exceptions</span></span>  
  
|<span data-ttu-id="bf244-119">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="bf244-119">Exception type</span></span>|<span data-ttu-id="bf244-120">Koşul</span><span class="sxs-lookup"><span data-stu-id="bf244-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="bf244-121">`Start` < = 0 veya `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="bf244-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf244-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf244-122">Remarks</span></span>  
 <span data-ttu-id="bf244-123">Değişen karakterlerin sayısı her zaman `Target` karakter sayısından küçüktür veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="bf244-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="bf244-124">Visual Basic bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işlevi ve bir `Mid` deyimidir.</span><span class="sxs-lookup"><span data-stu-id="bf244-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="bf244-125">Bu öğelerin her ikisi de bir dizedeki belirtilen sayıda karakter üzerinde çalışır, ancak `Mid` işlevi karakterleri, `Mid` ifadesinin yerini değiştirdiği halde döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf244-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="bf244-126">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf244-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf244-127">Önceki Visual Basic sürümlerindeki `MidB` deyimleri karakter yerine bayt cinsinden bir alt dizenin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="bf244-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="bf244-128">Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf244-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="bf244-129">Tüm Visual Basic dizeleri Unicode ve `MidB` artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="bf244-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf244-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf244-130">Example</span></span>  
 <span data-ttu-id="bf244-131">Bu örnek, bir dize değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterler ile değiştirmek için `Mid` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf244-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="bf244-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf244-132">Requirements</span></span>  
 <span data-ttu-id="bf244-133">**Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="bf244-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="bf244-134">**Modül:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="bf244-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="bf244-135">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="bf244-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf244-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf244-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="bf244-137">Dizeler</span><span class="sxs-lookup"><span data-stu-id="bf244-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="bf244-138">Visual Basic dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="bf244-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
