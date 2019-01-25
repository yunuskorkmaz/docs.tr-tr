---
title: '&lt;param&gt; - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: fb31e1d4c39888765fe3e55674d5b6d18b9d5b65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641024"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="ed371-102">&lt;param&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ed371-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ed371-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed371-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed371-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed371-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ed371-105">Bir yöntem parametresi adı.</span><span class="sxs-lookup"><span data-stu-id="ed371-105">The name of a method parameter.</span></span> <span data-ttu-id="ed371-106">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="ed371-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ed371-107">Parametre için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="ed371-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed371-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed371-108">Remarks</span></span>  
 <span data-ttu-id="ed371-109">\<Param > Etiket kullanılmalıdır yöntemi bildirimi için açıklama parametrelerden biri yöntemi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="ed371-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="ed371-110">Birden çok parametre belgeye birden çok kullanın \<param > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="ed371-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="ed371-111">Metni \<param > etiketi, IntelliSense, Nesne Tarayıcısı ve kod açıklaması Web rapor görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ed371-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="ed371-112">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="ed371-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed371-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed371-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ed371-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed371-114">See also</span></span>

- [<span data-ttu-id="ed371-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ed371-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ed371-116">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="ed371-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
