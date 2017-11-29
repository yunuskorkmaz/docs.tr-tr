---
title: "&lt;paramref&gt; (C# programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fff532c02538f121ebe399e1780d8c19d9d6633a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="1bf27-102">&lt;paramref&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1bf27-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1bf27-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bf27-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bf27-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bf27-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1bf27-105">Başvurmak için parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="1bf27-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="1bf27-106">Ad çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="1bf27-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bf27-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bf27-107">Remarks</span></span>  
 <span data-ttu-id="1bf27-108">\<Paramref > etiketi, kodda bir sözcük, örnekte yorum olduğunu belirtmek için bir yol verir bir \<Özet > veya \<açıklamalar > blok parametreye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="1bf27-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="1bf27-109">XML dosyası Bu word bazı farklı yolla gibi kalın veya Yatık yazı tipiyle Biçimlendirilecek işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="1bf27-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="1bf27-110">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="1bf27-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf27-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bf27-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1bf27-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf27-112">See Also</span></span>  
 [<span data-ttu-id="1bf27-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1bf27-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1bf27-114">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="1bf27-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
