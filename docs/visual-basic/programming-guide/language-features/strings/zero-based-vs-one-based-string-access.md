---
description: "Hakkında daha fazla bilgi edinin: Visual Basic 'de sıfır tabanlı ve tek tabanlı dize erişimi"
title: Sıfır tabanlı ve tek tabanlı dize erişimi
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: adab6954c4329ae0a547d136f26f6c3115dc5890
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463838"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="b8d2e-103">Visual Basic'de Sıfır Tabanlı ve Bir Tabanlı Dize Erişimi</span><span class="sxs-lookup"><span data-stu-id="b8d2e-103">Zero-based vs. One-based String Access in Visual Basic</span></span>

<span data-ttu-id="b8d2e-104">Bu konu, Visual Basic ve .NET Framework bir dizedeki karakterlere erişim sağlama şeklini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b8d2e-104">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="b8d2e-105">.NET Framework her zaman bir dizedeki karakterlere sıfır tabanlı erişim sağlar, ancak Visual Basic, işleve bağlı olarak sıfır tabanlı ve tek tabanlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8d2e-105">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="b8d2e-106">One-Based</span><span class="sxs-lookup"><span data-stu-id="b8d2e-106">One-Based</span></span>  

 <span data-ttu-id="b8d2e-107">Tek tabanlı Visual Basic işlevinin bir örneği için, işlevi göz önünde bulundurun `Mid` .</span><span class="sxs-lookup"><span data-stu-id="b8d2e-107">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="b8d2e-108">1. konumdan başlayarak alt dizenin başlayacağı karakter konumunu gösteren bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="b8d2e-108">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="b8d2e-109">.NET Framework yöntemi, alt <xref:System.String.Substring%2A?displayProperty=nameWithType> dizenin başlatılacağı dizedeki karakterin bir dizinini alır. konum 0 ' dan başlar.</span><span class="sxs-lookup"><span data-stu-id="b8d2e-109">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="b8d2e-110">Bu nedenle, "ABCDE" dizeniz varsa, tek tek karakterler 1, 2, 3, 4, işleviyle kullanım için 5, `Mid` 1, 2, 3, 4, yöntemiyle birlikte kullanılmak üzere numaralandırılır <xref:System.String.Substring%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b8d2e-110">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="b8d2e-111">Zero-Based</span><span class="sxs-lookup"><span data-stu-id="b8d2e-111">Zero-Based</span></span>  

 <span data-ttu-id="b8d2e-112">Sıfır tabanlı Visual Basic işlevinin bir örneği için, işlevi göz önünde bulundurun `Split` .</span><span class="sxs-lookup"><span data-stu-id="b8d2e-112">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="b8d2e-113">Bir dizeyi böler ve alt dizeleri içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8d2e-113">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="b8d2e-114">.NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi bir dizeyi de böler ve alt dizeleri içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8d2e-114">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="b8d2e-115">`Split`İşlev ve <xref:System.String.Split%2A> Yöntem .NET Framework diziler döndürdüğü için, bunların sıfır tabanlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8d2e-115">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d2e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8d2e-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="b8d2e-117">Visual Basic'de Dizelere Giriş</span><span class="sxs-lookup"><span data-stu-id="b8d2e-117">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
