---
title: <param> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: ffa3bd066ce753f2b953f2d6d0a70a3bf65293ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675942"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="604e0-102">\<param > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="604e0-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="604e0-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="604e0-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="604e0-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="604e0-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="604e0-105">Bir yöntem parametresi adı.</span><span class="sxs-lookup"><span data-stu-id="604e0-105">The name of a method parameter.</span></span> <span data-ttu-id="604e0-106">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="604e0-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="604e0-107">Parametre için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="604e0-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="604e0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="604e0-108">Remarks</span></span>  
 <span data-ttu-id="604e0-109">\<Param > Etiket kullanılmalıdır yöntemi bildirimi için açıklama parametrelerden biri yöntemi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="604e0-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="604e0-110">Birden çok parametre belgeye birden çok kullanın \<param > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="604e0-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="604e0-111">Metni \<param > etiketi, IntelliSense, Nesne Tarayıcısı ve kod açıklaması Web rapor görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="604e0-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="604e0-112">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="604e0-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="604e0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="604e0-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="604e0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="604e0-114">See also</span></span>

- [<span data-ttu-id="604e0-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="604e0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="604e0-116">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="604e0-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
