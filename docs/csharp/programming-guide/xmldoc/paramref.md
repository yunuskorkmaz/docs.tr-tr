---
title: <paramref>- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: e442b6829859ebc4dce6a0f5b6cd6cb777ab1400
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587912"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="b1c8d-102">\<paramref > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b1c8d-102">\<paramref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b1c8d-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1c8d-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1c8d-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1c8d-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b1c8d-105">Başvurabileceğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="b1c8d-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1c8d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1c8d-107">Remarks</span></span>  
 <span data-ttu-id="b1c8d-108">Paramref > etiketi, kod açıklamalarındaki bir sözcüğün, örneğin bir \<Özet > veya \<açıklamalar > bloğunun bir parametreye başvurduğunu göstermek için bir yol sağlar. \<</span><span class="sxs-lookup"><span data-stu-id="b1c8d-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="b1c8d-109">Bu sözcüğü, kalın veya italik yazı tipiyle olduğu gibi farklı bir şekilde biçimlendirmek için XML dosyası işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="b1c8d-110">Belge açıklamalarını bir dosyaya işlemek için [/doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1c8d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1c8d-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b1c8d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1c8d-112">See also</span></span>

- [<span data-ttu-id="b1c8d-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b1c8d-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b1c8d-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="b1c8d-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
