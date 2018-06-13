---
title: Mid Deyimi
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
ms.openlocfilehash: 90b805df902dcdfebe85421583dd54e9af04bec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602271"
---
# <a name="mid-statement"></a><span data-ttu-id="63256-102">Mid Deyimi</span><span class="sxs-lookup"><span data-stu-id="63256-102">Mid Statement</span></span>
<span data-ttu-id="63256-103">Belirtilen sayıda karakteri değiştiren bir `String` başka bir dizeden karakterleri içeren değişken.</span><span class="sxs-lookup"><span data-stu-id="63256-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63256-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63256-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="63256-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="63256-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="63256-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63256-106">Required.</span></span> <span data-ttu-id="63256-107">Adını `String` değiştirmek için değişken.</span><span class="sxs-lookup"><span data-stu-id="63256-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="63256-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63256-108">Required.</span></span> <span data-ttu-id="63256-109">`Integer` İfade.</span><span class="sxs-lookup"><span data-stu-id="63256-109">`Integer` expression.</span></span> <span data-ttu-id="63256-110">Karakter konumda `Target` metin değiştirme başladığı.</span><span class="sxs-lookup"><span data-stu-id="63256-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="63256-111">`Start` bir tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="63256-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="63256-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="63256-112">Optional.</span></span> <span data-ttu-id="63256-113">`Integer` İfade.</span><span class="sxs-lookup"><span data-stu-id="63256-113">`Integer` expression.</span></span> <span data-ttu-id="63256-114">Değiştirilecek karakterler sayısı.</span><span class="sxs-lookup"><span data-stu-id="63256-114">Number of characters to replace.</span></span> <span data-ttu-id="63256-115">Atlanırsa, tüm `String` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63256-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="63256-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63256-116">Required.</span></span> <span data-ttu-id="63256-117">`String` bölümünü değiştirir ifade `Target`.</span><span class="sxs-lookup"><span data-stu-id="63256-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="63256-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="63256-118">Exceptions</span></span>  
  
|<span data-ttu-id="63256-119">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="63256-119">Exception type</span></span>|<span data-ttu-id="63256-120">Koşul</span><span class="sxs-lookup"><span data-stu-id="63256-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="63256-121">`Start` < = 0 veya `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="63256-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63256-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63256-122">Remarks</span></span>  
 <span data-ttu-id="63256-123">Değiştirilen karakter sayısını her zaman karakter sayısı küçük veya buna eşit olan `Target`.</span><span class="sxs-lookup"><span data-stu-id="63256-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="63256-124">Visual Basic sahip bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işlevi ve `Mid` deyimi.</span><span class="sxs-lookup"><span data-stu-id="63256-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="63256-125">Her ikisi de çalışan bir dizedeki karakter belirtilen sayıdaki bu öğeleri ancak `Mid` işlevi sırasında karakter döndürür `Mid` deyimi karakterleri yerini alır.</span><span class="sxs-lookup"><span data-stu-id="63256-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="63256-126">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="63256-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63256-127">`MidB` Deyimi Visual Basic önceki sürümlerinin bir alt dizenin karakter yerine bayt yerini alır.</span><span class="sxs-lookup"><span data-stu-id="63256-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="63256-128">Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63256-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="63256-129">Tüm Visual Basic dizeleri Unicode biçiminde olan ve `MidB` artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="63256-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63256-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="63256-130">Example</span></span>  
 <span data-ttu-id="63256-131">Bu örnekte `Mid` başka bir dizeden karakterleri içeren bir dize değişkeni karakter belirtilen sayıda değiştirmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="63256-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="63256-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63256-132">Requirements</span></span>  
 <span data-ttu-id="63256-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="63256-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="63256-134">**Modülü:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="63256-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="63256-135">**Derleme:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63256-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63256-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63256-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="63256-137">Dizeler</span><span class="sxs-lookup"><span data-stu-id="63256-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="63256-138">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="63256-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
