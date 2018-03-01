---
title: "Sıfır tabanlı vs. Visual Basic'de dize tabanlı erişim"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="3c171-102">Sıfır tabanlı vs. Visual Basic'de dize tabanlı erişim</span><span class="sxs-lookup"><span data-stu-id="3c171-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="3c171-103">Bu konuda karşılaştırır nasıl [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bir dizedeki karakter erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c171-103">This topic compares how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="3c171-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Ancak her zaman bir dizedeki karakter sıfır tabanlı erişim sağlayan [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] işlevi bağlı olarak sıfır tabanlı ve tabanlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c171-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="3c171-105">Tabanlı</span><span class="sxs-lookup"><span data-stu-id="3c171-105">One-Based</span></span>  
 <span data-ttu-id="3c171-106">Bir tabanlı ilişkin bir örnek [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] işlev, göz önünde bulundurun `Mid` işlevi.</span><span class="sxs-lookup"><span data-stu-id="3c171-106">For an example of a one-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="3c171-107">Alt dizeyi, 1 konumundan başlayarak başlayacağı karakterin gösteren bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="3c171-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="3c171-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Yöntemi alır karakter dizinini alt dizeyi olduğu başlatmak için dizesinde başlama konumu 0 ile.</span><span class="sxs-lookup"><span data-stu-id="3c171-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="3c171-109">"ABCDE" dize varsa, bu nedenle, tek tek karakterleri 1,2,3,4,5 ile kullanmak için numaralandırılmış `Mid` işlevi ancak ile kullanılmak üzere 0,1,2,3,4 <xref:System.String.Substring%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3c171-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="3c171-110">Sıfır tabanlı</span><span class="sxs-lookup"><span data-stu-id="3c171-110">Zero-Based</span></span>  
 <span data-ttu-id="3c171-111">Sıfır tabanlı bir örneği için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] işlev, göz önünde bulundurun `Split` işlevi.</span><span class="sxs-lookup"><span data-stu-id="3c171-111">For an example of a zero-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="3c171-112">Bir dize böler ve alt dize içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c171-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="3c171-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi de bir dize böler ve alt dize içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c171-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="3c171-114">Çünkü `Split` işlevi ve <xref:System.String.Split%2A> yöntemi dönüş [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dizileri, bunlar olmalıdır sıfır tabanlı.</span><span class="sxs-lookup"><span data-stu-id="3c171-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c171-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c171-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [<span data-ttu-id="3c171-116">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="3c171-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
