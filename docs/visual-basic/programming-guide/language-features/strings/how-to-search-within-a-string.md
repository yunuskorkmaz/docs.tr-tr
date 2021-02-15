---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: dize içinde arama (Visual Basic)'
title: 'Nasıl yapılır: dize içinde arama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: dab9faf91eef2e6d845805693227e1a6735ec796
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429746"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="e15ed-103">Nasıl yapılır: dize içinde arama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e15ed-103">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="e15ed-104">Bu makalede, Visual Basic bir dize içinde aramanın nasıl yapılacağı hakkında bir örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e15ed-104">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="e15ed-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e15ed-105">Example</span></span>

<span data-ttu-id="e15ed-106">Bu örnek, bir alt <xref:System.String.IndexOf%2A> <xref:System.String> dizenin ilk geçtiği dizini raporlamak için bir nesne üzerindeki yöntemini çağırır:</span><span class="sxs-lookup"><span data-stu-id="e15ed-106">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="e15ed-107">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="e15ed-107">Robust programming</span></span>

<span data-ttu-id="e15ed-108">Yöntemi, alt <xref:System.String.IndexOf%2A> dizenin ilk örneğinin ilk karakterinin konumunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e15ed-108">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="e15ed-109">Dizin 0 tabanlıdır, yani bir dizenin ilk karakterinin 0 dizinine sahip olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e15ed-109">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="e15ed-110">Alt <xref:System.String.IndexOf%2A> dizeyi bulamazsa,-1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="e15ed-110">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="e15ed-111"><xref:System.String.IndexOf%2A>Yöntemi, büyük/küçük harfe duyarlıdır ve geçerli kültürü kullanır.</span><span class="sxs-lookup"><span data-stu-id="e15ed-111">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="e15ed-112">En iyi hata denetimi için, bir try bloğunda dize aramasını kapsamak isteyebilirsiniz.. `Try` [. Yakala... Finally deyiminin](../../../language-reference/statements/try-catch-finally-statement.md) oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="e15ed-112">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="e15ed-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e15ed-113">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="e15ed-114">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="e15ed-114">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="e15ed-115">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="e15ed-115">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="e15ed-116">Dizeler</span><span class="sxs-lookup"><span data-stu-id="e15ed-116">Strings</span></span>](index.md)
