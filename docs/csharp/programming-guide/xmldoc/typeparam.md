---
title: <typeparam> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 04145b82cbed0e9a5cae38ff9ef33d061ee792c9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694536"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="5cbb2-102">\<typeparam > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5cbb2-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="5cbb2-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cbb2-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cbb2-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cbb2-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5cbb2-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="5cbb2-105">The name of the type parameter.</span></span> <span data-ttu-id="5cbb2-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="5cbb2-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="5cbb2-107">Tür parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="5cbb2-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cbb2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cbb2-108">Remarks</span></span>  
 <span data-ttu-id="5cbb2-109">`<typeparam>` etiketi, bir tür parametresini betimleyen genel tür veya yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cbb2-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="5cbb2-110">Genel tür veya metodun her tür parametresi için bir etiket ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5cbb2-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="5cbb2-111">Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="5cbb2-111">For more information, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="5cbb2-112">`<typeparam>` etiketinin metni IntelliSense 'de, [nesne tarayıcısı pencere](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu açıklama Web raporunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5cbb2-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="5cbb2-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="5cbb2-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cbb2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cbb2-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="5cbb2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cbb2-115">See also</span></span>

- [<span data-ttu-id="5cbb2-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="5cbb2-116">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="5cbb2-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5cbb2-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5cbb2-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="5cbb2-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
