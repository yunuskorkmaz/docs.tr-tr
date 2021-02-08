---
description: 'Daha fazla bilgi edinin: MID ekstresi'
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
ms.openlocfilehash: 29cf933cb38fc6ef831570d0940b481abf9cfecf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768889"
---
# <a name="mid-statement"></a><span data-ttu-id="d0e4e-103">Mid Deyimi</span><span class="sxs-lookup"><span data-stu-id="d0e4e-103">Mid Statement</span></span>

<span data-ttu-id="d0e4e-104">Bir değişkende belirtilen sayıda karakteri `String` , başka bir dizeden karakterlerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-104">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e4e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0e4e-105">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="d0e4e-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d0e4e-106">Parts</span></span>  

 `Target`  
 <span data-ttu-id="d0e4e-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-107">Required.</span></span> <span data-ttu-id="d0e4e-108">`String`Değiştirilecek değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-108">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="d0e4e-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-109">Required.</span></span> <span data-ttu-id="d0e4e-110">`Integer` ifadesini.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-110">`Integer` expression.</span></span> <span data-ttu-id="d0e4e-111">`Target`Metnin yerini değiştirme işleminin başladığı karakter konumu.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-111">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="d0e4e-112">`Start` tek tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-112">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="d0e4e-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-113">Optional.</span></span> <span data-ttu-id="d0e4e-114">`Integer` ifadesini.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-114">`Integer` expression.</span></span> <span data-ttu-id="d0e4e-115">Değiştirilecek karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-115">Number of characters to replace.</span></span> <span data-ttu-id="d0e4e-116">Atlanırsa, tümü `String` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-116">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="d0e4e-117">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-117">Required.</span></span> <span data-ttu-id="d0e4e-118">`String` bölümünün yerini alan ifade `Target` .</span><span class="sxs-lookup"><span data-stu-id="d0e4e-118">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="d0e4e-119">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="d0e4e-119">Exceptions</span></span>  
  
|<span data-ttu-id="d0e4e-120">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="d0e4e-120">Exception type</span></span>|<span data-ttu-id="d0e4e-121">Koşul</span><span class="sxs-lookup"><span data-stu-id="d0e4e-121">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="d0e4e-122">`Start` <= 0 veya `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-122">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0e4e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0e4e-123">Remarks</span></span>  

 <span data-ttu-id="d0e4e-124">Değiştirilmekte olan karakter sayısı her zaman içindeki karakter sayısından daha küçüktür veya eşittir `Target` .</span><span class="sxs-lookup"><span data-stu-id="d0e4e-124">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="d0e4e-125">Visual Basic bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işleve ve ifadeye sahiptir `Mid` .</span><span class="sxs-lookup"><span data-stu-id="d0e4e-125">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="d0e4e-126">Bu öğeler her ikisi de bir dizedeki belirtilen sayıda karakter üzerinde çalışır, ancak işlev, `Mid` ifadenin karakterleri değiştirdiği sırada karakterleri döndürür `Mid` .</span><span class="sxs-lookup"><span data-stu-id="d0e4e-126">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="d0e4e-127">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-127">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0e4e-128">`MidB`Visual Basic önceki sürümleri, bir alt dizeyi karakterler yerine bayt olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-128">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="d0e4e-129">Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-129">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="d0e4e-130">Tüm Visual Basic dizeleri Unicode ve `MidB` artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-130">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0e4e-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0e4e-131">Example</span></span>  

 <span data-ttu-id="d0e4e-132">Bu örnek, bir `Mid` dize değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterler ile değiştirmek için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-132">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="d0e4e-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0e4e-133">Requirements</span></span>  

 <span data-ttu-id="d0e4e-134">**Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="d0e4e-134">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="d0e4e-135">**Modül:**`Strings`</span><span class="sxs-lookup"><span data-stu-id="d0e4e-135">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="d0e4e-136">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="d0e4e-136">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e4e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0e4e-137">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="d0e4e-138">Dizeler</span><span class="sxs-lookup"><span data-stu-id="d0e4e-138">Strings</span></span>](../../programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="d0e4e-139">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="d0e4e-139">Introduction to Strings in Visual Basic</span></span>](../../programming-guide/language-features/strings/introduction-to-strings.md)
