---
title: <param> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: f9613a7373a829d2a52f3f56b8ea1ab35ebdcf5f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711733"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="af1ab-102">\<param > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="af1ab-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="af1ab-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af1ab-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="af1ab-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af1ab-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="af1ab-105">Bir yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="af1ab-105">The name of a method parameter.</span></span> <span data-ttu-id="af1ab-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="af1ab-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="af1ab-107">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="af1ab-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af1ab-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af1ab-108">Remarks</span></span>  
 <span data-ttu-id="af1ab-109">Yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimi için açıklamasında \<param > etiketi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af1ab-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="af1ab-110">Birden çok parametreyi belgelemek için, birden çok \<param > etiketi kullanın.</span><span class="sxs-lookup"><span data-stu-id="af1ab-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="af1ab-111">\<param > etiketinin metni IntelliSense 'de, Nesne Tarayıcısı ve kod yorumu Web raporunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="af1ab-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="af1ab-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="af1ab-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af1ab-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="af1ab-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="af1ab-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af1ab-114">See also</span></span>

- [<span data-ttu-id="af1ab-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="af1ab-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="af1ab-116">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="af1ab-116">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
