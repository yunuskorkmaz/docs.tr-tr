---
description: 'Hakkında daha fazla bilgi edinin: <inheritdoc> (C# Programlama Kılavuzu)'
title: <inheritdoc> -C# Programlama Kılavuzu
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 960bdfbcec1e3f6a89675273f63b6d398e44947e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719402"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="37f34-103">\<inheritdoc> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="37f34-103">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="37f34-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="37f34-104">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="37f34-105">Devralma belgesi</span><span class="sxs-lookup"><span data-stu-id="37f34-105">InheritDoc</span></span>

<span data-ttu-id="37f34-106">Temel sınıflardan, arabirimlerden ve benzer metotlardan XML açıklamalarını devralma.</span><span class="sxs-lookup"><span data-stu-id="37f34-106">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="37f34-107">Bu, yinelenen XML açıklamalarını istenmeyen kopyalama ve yapıştırmayı ortadan kaldırır ve otomatik olarak XML açıklamalarını eşitlenmiş halde tutar.</span><span class="sxs-lookup"><span data-stu-id="37f34-107">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="37f34-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37f34-108">Remarks</span></span>  

<span data-ttu-id="37f34-109">XML yorumlarınızı temel sınıflara veya arabirimlere ekleyin ve ınherıng doc 'in, sınıfları uygulama açıklamalarını kopyalamasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="37f34-109">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="37f34-110">XML yorumlarınızı zaman uyumlu yöntemlerinize ekleyin ve ınherelidoc 'in açıklamaları aynı yöntemlerin zaman uyumsuz sürümlerine kopyalamasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="37f34-110">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="37f34-111">Belirli bir üyeden açıklamaları kopyalamak istiyorsanız, `cref` üyeyi belirtmek için özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37f34-111">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="37f34-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="37f34-112">Examples</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="37f34-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37f34-113">See also</span></span>

- [<span data-ttu-id="37f34-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="37f34-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="37f34-115">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="37f34-115">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
