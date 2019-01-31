---
title: <paramref> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4fd0770bfe6c15c0e9b10239019ec265550dc372
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262841"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="c93ba-102">\<paramref > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c93ba-102">\<paramref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c93ba-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c93ba-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c93ba-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c93ba-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c93ba-105">Başvurmak için parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="c93ba-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="c93ba-106">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="c93ba-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c93ba-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c93ba-107">Remarks</span></span>  
 <span data-ttu-id="c93ba-108">\<Paramref > etiketi kodda bir sözcük, örnekte yorum olduğunu göstermek için bir yol sağlar bir \<Özet > veya \<remarks > blok bir parametresine başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="c93ba-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="c93ba-109">XML dosyası, bu sözcüğü biçimlendirmek kalın veya Yatık yazı tipiyle farklı şekilde, gibi için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c93ba-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="c93ba-110">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="c93ba-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c93ba-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c93ba-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c93ba-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c93ba-112">See also</span></span>

- [<span data-ttu-id="c93ba-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c93ba-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c93ba-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="c93ba-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
