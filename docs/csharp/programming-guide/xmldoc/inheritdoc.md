---
title: <inheritdoc> C# Programlama Kılavuzu
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d660cb1739733c4e98ae0b7939476fe74e6cf200
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795163"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="9e5b9-102">\<ınherbir doc >C# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9e5b9-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9e5b9-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e5b9-103">Syntax</span></span>  
  
```xml  
<inheritdoc/> 
```  

## <a name="inheritdoc"></a><span data-ttu-id="9e5b9-104">Devralma belgesi</span><span class="sxs-lookup"><span data-stu-id="9e5b9-104">InheritDoc</span></span>

<span data-ttu-id="9e5b9-105">Temel sınıflardan, arabirimlerden ve benzer metotlardan XML açıklamalarını devralma.</span><span class="sxs-lookup"><span data-stu-id="9e5b9-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="9e5b9-106">Bu, yinelenen XML açıklamalarını istenmeyen kopyalama ve yapıştırmayı ortadan kaldırır ve otomatik olarak XML açıklamalarını eşitlenmiş halde tutar.</span><span class="sxs-lookup"><span data-stu-id="9e5b9-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="9e5b9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e5b9-107">Remarks</span></span>  
<span data-ttu-id="9e5b9-108">XML yorumlarınızı temel sınıflara veya arabirimlere ekleyin ve ınherıng doc 'in, sınıfları uygulama açıklamalarını kopyalamasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="9e5b9-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="9e5b9-109">XML yorumlarınızı zaman uyumlu yöntemlerinize ekleyin ve ınherelidoc 'in açıklamaları aynı yöntemlerin zaman uyumsuz sürümlerine kopyalamasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9e5b9-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="9e5b9-110">Belirli bir üyeden açıklamaları kopyalamak istiyorsanız, üyeyi belirtmek için `cref` özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e5b9-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="9e5b9-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9e5b9-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="9e5b9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e5b9-112">See also</span></span>

- [<span data-ttu-id="9e5b9-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9e5b9-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9e5b9-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="9e5b9-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
