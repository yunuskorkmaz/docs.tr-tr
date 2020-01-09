---
title: 'Nasıl yapılır: dize içinde arama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 655f746e4e496e1935afcd2a9f9fe36d9e3a2564
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348417"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="e6579-102">Nasıl yapılır: dize içinde arama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6579-102">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="e6579-103">Bu makalede, Visual Basic bir dize içinde aramanın nasıl yapılacağı hakkında bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e6579-103">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="e6579-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6579-104">Example</span></span>

<span data-ttu-id="e6579-105">Bu örnek, bir alt dizenin ilk geçtiği dizini raporlamak için bir <xref:System.String> nesnesindeki <xref:System.String.IndexOf%2A> yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="e6579-105">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="e6579-106">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="e6579-106">Robust programming</span></span>

<span data-ttu-id="e6579-107"><xref:System.String.IndexOf%2A> yöntemi, alt dizenin ilk oluşumunun ilk karakterinin konumunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e6579-107">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="e6579-108">Dizin 0 tabanlıdır, yani bir dizenin ilk karakterinin 0 dizinine sahip olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e6579-108">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="e6579-109"><xref:System.String.IndexOf%2A> alt dizeyi bulamazsa,-1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="e6579-109">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="e6579-110"><xref:System.String.IndexOf%2A> yöntemi, büyük/küçük harfe duyarlıdır ve geçerli kültürü kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6579-110">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="e6579-111">En iyi hata denetimi için, bir TRY `Try` bloğunda dize aramasını kapsamak isteyebilirsiniz [... Yakala... Finally deyiminin](../../../language-reference/statements/try-catch-finally-statement.md) oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="e6579-111">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6579-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6579-112">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="e6579-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="e6579-113">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="e6579-114">Visual Basic dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="e6579-114">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="e6579-115">Dizeler</span><span class="sxs-lookup"><span data-stu-id="e6579-115">Strings</span></span>](index.md)
