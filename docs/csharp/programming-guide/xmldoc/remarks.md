---
title: <remarks> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 508201fed57fce93b64691de55dce45780adc13c
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523349"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="7abb1-102">\<remarks > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7abb1-102">\<remarks> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="7abb1-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7abb1-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7abb1-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7abb1-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="7abb1-105">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="7abb1-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7abb1-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7abb1-106">Remarks</span></span>  
 <span data-ttu-id="7abb1-107">@No__t_0remarks > etiketi, [\<summary >](./summary.md)ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7abb1-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="7abb1-108">Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7abb1-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="7abb1-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="7abb1-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7abb1-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7abb1-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="7abb1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7abb1-111">See also</span></span>

- [<span data-ttu-id="7abb1-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7abb1-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7abb1-113">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="7abb1-113">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
