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
ms.openlocfilehash: df83fd527612af1a6a4b8131ffa2643ef0d1d7dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784245"
---
# <a name="mid-statement"></a><span data-ttu-id="19887-102">Mid Deyimi</span><span class="sxs-lookup"><span data-stu-id="19887-102">Mid Statement</span></span>
<span data-ttu-id="19887-103">Belirtilen sayıda karakter yerini alan bir `String` başka bir dizeden karakterlerle değişken.</span><span class="sxs-lookup"><span data-stu-id="19887-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19887-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19887-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="19887-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="19887-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="19887-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="19887-106">Required.</span></span> <span data-ttu-id="19887-107">Adını `String` değiştirmek için değişken.</span><span class="sxs-lookup"><span data-stu-id="19887-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="19887-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="19887-108">Required.</span></span> <span data-ttu-id="19887-109">`Integer` ifade.</span><span class="sxs-lookup"><span data-stu-id="19887-109">`Integer` expression.</span></span> <span data-ttu-id="19887-110">Karakter konumunda `Target` burada metin değiştirmesinin.</span><span class="sxs-lookup"><span data-stu-id="19887-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="19887-111">`Start` bir tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="19887-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="19887-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="19887-112">Optional.</span></span> <span data-ttu-id="19887-113">`Integer` ifade.</span><span class="sxs-lookup"><span data-stu-id="19887-113">`Integer` expression.</span></span> <span data-ttu-id="19887-114">Değiştirilecek karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="19887-114">Number of characters to replace.</span></span> <span data-ttu-id="19887-115">Atlanırsa, tüm `String` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19887-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="19887-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="19887-116">Required.</span></span> <span data-ttu-id="19887-117">`String` bölümünü değiştirir ifade `Target`.</span><span class="sxs-lookup"><span data-stu-id="19887-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="19887-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="19887-118">Exceptions</span></span>  
  
|<span data-ttu-id="19887-119">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="19887-119">Exception type</span></span>|<span data-ttu-id="19887-120">Koşul</span><span class="sxs-lookup"><span data-stu-id="19887-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="19887-121">`Start` < = 0 veya `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="19887-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19887-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19887-122">Remarks</span></span>  
 <span data-ttu-id="19887-123">Değiştirilen karakter sayısını her zaman eşit veya karakter sayısı küçüktür `Target`.</span><span class="sxs-lookup"><span data-stu-id="19887-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="19887-124">Visual Basic sahip bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işlevi ve bir `Mid` deyimi.</span><span class="sxs-lookup"><span data-stu-id="19887-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="19887-125">Bu öğelerden hem de çalışan bir belirtilen bir dizedeki karakter sayısına ancak `Mid` işlevi çalışırken karakterleri döndürür `Mid` deyimi karakterleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="19887-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="19887-126">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="19887-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19887-127">`MidB` Visual Basic'in önceki sürümlerindeki deyiminin karakter yerine bayt bir alt dizeyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="19887-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="19887-128">Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19887-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="19887-129">Tüm Visual Basic dizeleri Unicode biçimindedir ve `MidB` artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="19887-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19887-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="19887-130">Example</span></span>  
 <span data-ttu-id="19887-131">Bu örnekte `Mid` deyimi başka bir dizeden karakterlerle belirtilen sayıda karakteri bir dize değişkeniyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="19887-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="19887-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19887-132">Requirements</span></span>  
 <span data-ttu-id="19887-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="19887-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="19887-134">**Modül:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="19887-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="19887-135">**Derleme:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19887-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19887-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19887-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="19887-137">Dizeler</span><span class="sxs-lookup"><span data-stu-id="19887-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="19887-138">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="19887-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
