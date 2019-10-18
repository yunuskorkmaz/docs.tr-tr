---
title: <c> C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 9454ef8cc4b72d1d6bdcac26faf76eb17080328c
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523537"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="b75f6-102">\<c > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b75f6-102">\<c> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b75f6-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b75f6-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b75f6-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b75f6-104">Parameters</span></span>  
 `text`  
 <span data-ttu-id="b75f6-105">Kod olarak göstermek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="b75f6-105">The text you would like to indicate as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b75f6-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b75f6-106">Remarks</span></span>  
 <span data-ttu-id="b75f6-107">@No__t_0c > etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b75f6-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="b75f6-108">Birden çok satırı kod olarak göstermek için [\<code >](./code.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b75f6-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="b75f6-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="b75f6-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b75f6-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b75f6-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b75f6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b75f6-111">See also</span></span>

- [<span data-ttu-id="b75f6-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b75f6-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b75f6-113">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="b75f6-113">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
