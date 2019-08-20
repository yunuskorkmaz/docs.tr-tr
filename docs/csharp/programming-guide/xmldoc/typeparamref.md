---
title: <typeparamref>- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: f01df27b920dcf3011a51015c771d2da3b442c4c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587421"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="27bd2-102">\<typeparamref > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="27bd2-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="27bd2-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27bd2-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="27bd2-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27bd2-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="27bd2-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="27bd2-105">The name of the type parameter.</span></span> <span data-ttu-id="27bd2-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="27bd2-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27bd2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27bd2-107">Remarks</span></span>  
 <span data-ttu-id="27bd2-108">Genel türlerde ve yöntemlerde tür parametreleri hakkında daha fazla bilgi için bkz. [Genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="27bd2-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="27bd2-109">Belge dosyasının tüketicilerini farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlamak için bu etiketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="27bd2-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="27bd2-110">Belge açıklamalarını bir dosyaya işlemek için [/doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="27bd2-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27bd2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="27bd2-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="27bd2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27bd2-112">See also</span></span>

- [<span data-ttu-id="27bd2-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="27bd2-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="27bd2-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="27bd2-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
