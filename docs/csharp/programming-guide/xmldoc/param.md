---
title: '&lt;param&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 3d89637e5b1238c582390750e8eef30960fa90b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338019"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="e1cdf-102">&lt;param&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e1cdf-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e1cdf-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1cdf-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1cdf-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1cdf-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e1cdf-105">Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-105">The name of a method parameter.</span></span> <span data-ttu-id="e1cdf-106">Ad çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="e1cdf-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="e1cdf-107">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1cdf-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1cdf-108">Remarks</span></span>  
 <span data-ttu-id="e1cdf-109">\<Param > etiketi açıklamasında bir yöntem bildirimi için parametrelerden biri yönteminde açıklamak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="e1cdf-110">Birden çok parametre belgelemek için birden çok kullanmak \<param > etiketler.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="e1cdf-111">Metni \<param > etiketi, IntelliSense, Nesne Tarayıcısı ve kod açıklama Web raporu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="e1cdf-112">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1cdf-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1cdf-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e1cdf-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1cdf-114">See Also</span></span>  
 [<span data-ttu-id="e1cdf-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e1cdf-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e1cdf-116">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="e1cdf-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
