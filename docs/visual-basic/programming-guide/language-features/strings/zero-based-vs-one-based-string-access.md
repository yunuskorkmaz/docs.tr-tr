---
title: Sıfır Tabanlı ve Visual Basic'te bir tabanlı dize erişimi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a6ceb10d4a3cb9463551d8c85375ddbbb607ffdc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830337"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="5d1f2-102">Sıfır Tabanlı ve Visual Basic'te bir tabanlı dize erişimi</span><span class="sxs-lookup"><span data-stu-id="5d1f2-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="5d1f2-103">Bu konu Visual Basic karşılaştırır ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bir dizedeki karakter erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-103">This topic compares how Visual Basic and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="5d1f2-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Visual Basic işlevi bağlı olarak, sıfır tabanlı ve bir tabanlı erişim sağlar ancak her zaman bir dizedeki karakter sıfır tabanlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="5d1f2-105">Bir tabanlı</span><span class="sxs-lookup"><span data-stu-id="5d1f2-105">One-Based</span></span>  
 <span data-ttu-id="5d1f2-106">Visual Basic bir tabanlı işlevi örneği için göz önünde bulundurun `Mid` işlevi.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="5d1f2-107">İşlem alt dizeyi, konum 1 ile başlayan başlayacağı karakter konumunu belirten bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="5d1f2-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Yöntemi alır karakter dizinini alt dizeyi olduğu başlatmak için dizedeki başlangıç konumu 0 ile.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="5d1f2-109">Bu nedenle, bir dize "ABCDE" varsa, karakterlerin tek tek ile kullanılmak üzere 1,2,3,4,5 numaralandırılır `Mid` işlevi, ancak ile kullanılmak üzere 0,1,2,3,4 <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="5d1f2-110">Sıfır tabanlı</span><span class="sxs-lookup"><span data-stu-id="5d1f2-110">Zero-Based</span></span>  
 <span data-ttu-id="5d1f2-111">Sıfır tabanlı bir Visual Basic işlev örneği için göz önünde bulundurun `Split` işlevi.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="5d1f2-112">Bir dizeyi böler ve alt dizeler içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5d1f2-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi ayrıca bir dizeyi böler ve alt dizeler içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5d1f2-114">Çünkü `Split` işlevi ve <xref:System.String.Split%2A> yöntemi dönüş [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] diziler, bunlar olmalıdır sıfır tabanlı.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1f2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d1f2-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="5d1f2-116">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="5d1f2-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
