---
title: <inheritdoc>- C# Programlama Kılavuzu
ms.date: 01/21/2020
f1_keywords:
- inheritdoc
- <inheritdoc>
helpviewer_keywords:
- <inheritdoc> C# XML tag
- inheritdoc C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 6f42462f21d045428577cd2123e2180d866f1e1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156954"
---
# <a name="inheritdoc-c-programming-guide"></a><span data-ttu-id="500b9-102">\<inheritdoc> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="500b9-102">\<inheritdoc> (C# Programming Guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="500b9-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="500b9-103">Syntax</span></span>  
  
```xml  
<inheritdoc/>
```  

## <a name="inheritdoc"></a><span data-ttu-id="500b9-104">Kalıtsal Doküman</span><span class="sxs-lookup"><span data-stu-id="500b9-104">InheritDoc</span></span>

<span data-ttu-id="500b9-105">Temel sınıflardan, arabirimlerden ve benzer yöntemlerden XML yorumlarını devredin.</span><span class="sxs-lookup"><span data-stu-id="500b9-105">Inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="500b9-106">Bu, yinelenen XML yorumlarının istenmeyen kopyalanması ve yapıştırMasını ortadan kaldırır ve XML yorumlarını otomatik olarak senkronize eder.</span><span class="sxs-lookup"><span data-stu-id="500b9-106">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="500b9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="500b9-107">Remarks</span></span>  
<span data-ttu-id="500b9-108">XML yorumlarınızı temel sınıflara veya arabirimlere ekleyin ve InheritDoc'un açıklamaları uygulama sınıflarına kopyalamasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="500b9-108">Add your XML comments in base classes or interfaces and let InheritDoc copy the comments to implementing classes.</span></span>

<span data-ttu-id="500b9-109">XML yorumlarınızı eşzamanlı yöntemlerinize ekleyin ve InheritDoc'un yorumları aynı yöntemlerin eşzamanlı sürümlerine kopyalamasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="500b9-109">Add your XML comments to your synchronous methods and let InheritDoc copy the comments to your asynchronous versions of the same methods.</span></span>  

<span data-ttu-id="500b9-110">Belirli bir üyenin yorumlarını kopyalamak istiyorsanız, `cref` üyeyi belirtmek için özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="500b9-110">If you want to copy the comments from a specific member you can use the `cref` attribute to specify the member.</span></span>
  
## <a name="examples"></a><span data-ttu-id="500b9-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="500b9-111">Examples</span></span>
[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#16)]  

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#17)]  

## <a name="see-also"></a><span data-ttu-id="500b9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="500b9-112">See also</span></span>

- [<span data-ttu-id="500b9-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="500b9-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="500b9-114">Dokümantasyon Yorumları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="500b9-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
