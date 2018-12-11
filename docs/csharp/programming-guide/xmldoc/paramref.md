---
title: '&lt;paramref&gt; - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 90c22b81f17adb1fcfdb94f32047e85c0bd8f4e5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243638"
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="fc80f-102">&lt;paramref&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fc80f-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="fc80f-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc80f-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc80f-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc80f-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fc80f-105">Başvurmak için parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="fc80f-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="fc80f-106">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="fc80f-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc80f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc80f-107">Remarks</span></span>  
 <span data-ttu-id="fc80f-108">\<Paramref > etiketi kodda bir sözcük, örnekte yorum olduğunu göstermek için bir yol sağlar bir \<Özet > veya \<remarks > blok bir parametresine başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="fc80f-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="fc80f-109">XML dosyası, bu sözcüğü biçimlendirmek kalın veya Yatık yazı tipiyle farklı şekilde, gibi için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="fc80f-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="fc80f-110">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="fc80f-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc80f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc80f-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fc80f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc80f-112">See Also</span></span>

- [<span data-ttu-id="fc80f-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fc80f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fc80f-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="fc80f-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
