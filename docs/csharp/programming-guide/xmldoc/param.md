---
title: '&lt;param&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: b4afa84aadc68ca2f0113023319f02a10dc17836
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508221"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="b373d-102">&lt;param&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b373d-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b373d-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b373d-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b373d-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b373d-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b373d-105">Bir yöntem parametresi adı.</span><span class="sxs-lookup"><span data-stu-id="b373d-105">The name of a method parameter.</span></span> <span data-ttu-id="b373d-106">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="b373d-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="b373d-107">Parametre için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="b373d-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b373d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b373d-108">Remarks</span></span>  
 <span data-ttu-id="b373d-109">\<Param > Etiket kullanılmalıdır yöntemi bildirimi için açıklama parametrelerden biri yöntemi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="b373d-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="b373d-110">Birden çok parametre belgeye birden çok kullanın \<param > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="b373d-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="b373d-111">Metni \<param > etiketi, IntelliSense, Nesne Tarayıcısı ve kod açıklaması Web rapor görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b373d-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="b373d-112">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="b373d-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b373d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b373d-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b373d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b373d-114">See Also</span></span>

- [<span data-ttu-id="b373d-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b373d-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b373d-116">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="b373d-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
