---
title: <typeparam> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 9150ab3e29eaa6b692e2ab2be90bb0e87ba54941
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978668"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="6a652-102">\<typeparam > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6a652-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="6a652-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a652-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a652-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a652-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6a652-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="6a652-105">The name of the type parameter.</span></span> <span data-ttu-id="6a652-106">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="6a652-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6a652-107">Tür parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="6a652-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a652-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a652-108">Remarks</span></span>  
 <span data-ttu-id="6a652-109">`<typeparam>` Etiketi genel bir tür veya yöntem bildirimi için açıklama açıklayan bir tür parametresi için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a652-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="6a652-110">Genel tür veya yöntemin her tür parametresi için bir etiket ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6a652-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="6a652-111">Daha fazla bilgi için [genel türler](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a652-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="6a652-112">Metni `<typeparam>` etiketi IntelliSense içinde gösterilecek [nesne tarayıcı penceresi](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kod açıklaması web rapor.</span><span class="sxs-lookup"><span data-stu-id="6a652-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="6a652-113">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="6a652-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a652-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a652-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="6a652-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a652-115">See also</span></span>

- [<span data-ttu-id="6a652-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6a652-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="6a652-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6a652-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6a652-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="6a652-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
