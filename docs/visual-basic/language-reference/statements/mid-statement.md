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
ms.openlocfilehash: 90408fd8a8cfc9b74c8422d0571d61f8534403f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404465"
---
# <a name="mid-statement"></a><span data-ttu-id="31d08-102">Mid Deyimi</span><span class="sxs-lookup"><span data-stu-id="31d08-102">Mid Statement</span></span>
<span data-ttu-id="31d08-103">Bir değişkende belirtilen sayıda karakteri `String` , başka bir dizeden karakterlerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="31d08-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31d08-104">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="31d08-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="31d08-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="31d08-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31d08-106">Required.</span></span> <span data-ttu-id="31d08-107">`String`Değiştirilecek değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="31d08-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="31d08-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31d08-108">Required.</span></span> <span data-ttu-id="31d08-109">`Integer`ifadesini.</span><span class="sxs-lookup"><span data-stu-id="31d08-109">`Integer` expression.</span></span> <span data-ttu-id="31d08-110">`Target`Metnin yerini değiştirme işleminin başladığı karakter konumu.</span><span class="sxs-lookup"><span data-stu-id="31d08-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="31d08-111">`Start`tek tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="31d08-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="31d08-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="31d08-112">Optional.</span></span> <span data-ttu-id="31d08-113">`Integer`ifadesini.</span><span class="sxs-lookup"><span data-stu-id="31d08-113">`Integer` expression.</span></span> <span data-ttu-id="31d08-114">Değiştirilecek karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="31d08-114">Number of characters to replace.</span></span> <span data-ttu-id="31d08-115">Atlanırsa, tümü `String` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31d08-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="31d08-116">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="31d08-116">Required.</span></span> <span data-ttu-id="31d08-117">`String`bölümünün yerini alan ifade `Target` .</span><span class="sxs-lookup"><span data-stu-id="31d08-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="31d08-118">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="31d08-118">Exceptions</span></span>  
  
|<span data-ttu-id="31d08-119">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="31d08-119">Exception type</span></span>|<span data-ttu-id="31d08-120">Koşul</span><span class="sxs-lookup"><span data-stu-id="31d08-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="31d08-121">`Start`<= 0 veya `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="31d08-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31d08-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31d08-122">Remarks</span></span>  
 <span data-ttu-id="31d08-123">Değiştirilmekte olan karakter sayısı her zaman içindeki karakter sayısından daha küçüktür veya eşittir `Target` .</span><span class="sxs-lookup"><span data-stu-id="31d08-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="31d08-124">Visual Basic bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işleve ve ifadeye sahiptir `Mid` .</span><span class="sxs-lookup"><span data-stu-id="31d08-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="31d08-125">Bu öğeler her ikisi de bir dizedeki belirtilen sayıda karakter üzerinde çalışır, ancak işlev, `Mid` ifadenin karakterleri değiştirdiği sırada karakterleri döndürür `Mid` .</span><span class="sxs-lookup"><span data-stu-id="31d08-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="31d08-126">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="31d08-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31d08-127">`MidB`Visual Basic önceki sürümleri, bir alt dizeyi karakterler yerine bayt olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="31d08-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="31d08-128">Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31d08-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="31d08-129">Tüm Visual Basic dizeleri Unicode ve `MidB` artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="31d08-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31d08-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="31d08-130">Example</span></span>  
 <span data-ttu-id="31d08-131">Bu örnek, bir `Mid` dize değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterler ile değiştirmek için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="31d08-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="31d08-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31d08-132">Requirements</span></span>  
 <span data-ttu-id="31d08-133">**Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="31d08-133">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="31d08-134">**Modül:**`Strings`</span><span class="sxs-lookup"><span data-stu-id="31d08-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="31d08-135">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="31d08-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d08-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31d08-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="31d08-137">Dizeler</span><span class="sxs-lookup"><span data-stu-id="31d08-137">Strings</span></span>](../../programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="31d08-138">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="31d08-138">Introduction to Strings in Visual Basic</span></span>](../../programming-guide/language-features/strings/introduction-to-strings.md)
