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
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963545"
---
# <a name="mid-statement"></a><span data-ttu-id="4a22e-102">Mid Deyimi</span><span class="sxs-lookup"><span data-stu-id="4a22e-102">Mid Statement</span></span>
<span data-ttu-id="4a22e-103">Bir `String` değişkende belirtilen sayıda karakteri, başka bir dizeden karakterlerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4a22e-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a22e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a22e-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="4a22e-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4a22e-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="4a22e-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4a22e-106">Required.</span></span> <span data-ttu-id="4a22e-107">`String` Değiştirilecek değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="4a22e-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="4a22e-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4a22e-108">Required.</span></span> <span data-ttu-id="4a22e-109">`Integer`ifadesini.</span><span class="sxs-lookup"><span data-stu-id="4a22e-109">`Integer` expression.</span></span> <span data-ttu-id="4a22e-110">Metnin yerini değiştirme `Target` işleminin başladığı karakter konumu.</span><span class="sxs-lookup"><span data-stu-id="4a22e-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="4a22e-111">`Start`tek tabanlı bir dizin kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a22e-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="4a22e-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4a22e-112">Optional.</span></span> <span data-ttu-id="4a22e-113">`Integer`ifadesini.</span><span class="sxs-lookup"><span data-stu-id="4a22e-113">`Integer` expression.</span></span> <span data-ttu-id="4a22e-114">Değiştirilecek karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="4a22e-114">Number of characters to replace.</span></span> <span data-ttu-id="4a22e-115">Atlanırsa, tümü `String` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a22e-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="4a22e-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4a22e-116">Required.</span></span> <span data-ttu-id="4a22e-117">`String`bölümünün yerini alan ifade `Target`.</span><span class="sxs-lookup"><span data-stu-id="4a22e-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="4a22e-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="4a22e-118">Exceptions</span></span>  
  
|<span data-ttu-id="4a22e-119">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="4a22e-119">Exception type</span></span>|<span data-ttu-id="4a22e-120">Koşul</span><span class="sxs-lookup"><span data-stu-id="4a22e-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="4a22e-121">`Start`< = 0 veya `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="4a22e-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a22e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a22e-122">Remarks</span></span>  
 <span data-ttu-id="4a22e-123">Değiştirilmekte olan karakter sayısı her zaman içindeki `Target`karakter sayısından daha küçüktür veya eşittir.</span><span class="sxs-lookup"><span data-stu-id="4a22e-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="4a22e-124">Visual Basic bir <xref:Microsoft.VisualBasic.Strings.Mid%2A> işleve `Mid` ve ifadeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4a22e-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="4a22e-125">Bu öğeler her ikisi de bir dizedeki belirtilen sayıda karakter üzerinde çalışır, ancak `Mid` işlev, `Mid` ifadenin karakterleri değiştirdiği sırada karakterleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a22e-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="4a22e-126">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a22e-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a22e-127">Visual Basic `MidB` önceki sürümleri, bir alt dizeyi karakterler yerine bayt olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4a22e-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="4a22e-128">Esas olarak çift baytlı karakter kümesi (DBCS) uygulamalarında dize dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a22e-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="4a22e-129">Tüm Visual Basic dizeleri Unicode ve `MidB` artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4a22e-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a22e-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a22e-130">Example</span></span>  
 <span data-ttu-id="4a22e-131">Bu örnek, `Mid` bir dize değişkeninde belirtilen sayıda karakteri başka bir dizeden karakterler ile değiştirmek için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a22e-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="4a22e-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a22e-132">Requirements</span></span>  
 <span data-ttu-id="4a22e-133">**Uzayına** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="4a22e-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="4a22e-134">**Modül:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="4a22e-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="4a22e-135">**Derleme** Visual Basic Çalışma Zamanı Kitaplığı (Microsoft.VisualBasic.dll içinde)</span><span class="sxs-lookup"><span data-stu-id="4a22e-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a22e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a22e-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="4a22e-137">Dizeler</span><span class="sxs-lookup"><span data-stu-id="4a22e-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="4a22e-138">Visual Basic dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="4a22e-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
