---
title: "&lt;param&gt; (C# programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a5325b91130623442c9cf5453e52418bb44cc34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="69b72-102">&lt;param&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="69b72-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="69b72-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69b72-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69b72-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69b72-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="69b72-105">Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="69b72-105">The name of a method parameter.</span></span> <span data-ttu-id="69b72-106">Ad çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="69b72-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="69b72-107">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="69b72-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69b72-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69b72-108">Remarks</span></span>  
 <span data-ttu-id="69b72-109">\<Param > etiketi açıklamasında bir yöntem bildirimi için parametrelerden biri yönteminde açıklamak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69b72-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="69b72-110">Birden çok parametre belgelemek için birden çok kullanmak \<param > etiketler.</span><span class="sxs-lookup"><span data-stu-id="69b72-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="69b72-111">Metni \<param > etiketi, IntelliSense, Nesne Tarayıcısı ve kod açıklama Web raporu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="69b72-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="69b72-112">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="69b72-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69b72-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="69b72-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="69b72-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69b72-114">See Also</span></span>  
 [<span data-ttu-id="69b72-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="69b72-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="69b72-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="69b72-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
