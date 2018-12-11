---
title: '&lt;param&gt; - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: fca53a3cd5490c28c8fabcf69446fe4a55d60b4e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236966"
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="f8c47-102">&lt;param&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f8c47-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="f8c47-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8c47-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8c47-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f8c47-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f8c47-105">Bir yöntem parametresi adı.</span><span class="sxs-lookup"><span data-stu-id="f8c47-105">The name of a method parameter.</span></span> <span data-ttu-id="f8c47-106">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="f8c47-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="f8c47-107">Parametre için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="f8c47-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8c47-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8c47-108">Remarks</span></span>  
 <span data-ttu-id="f8c47-109">\<Param > Etiket kullanılmalıdır yöntemi bildirimi için açıklama parametrelerden biri yöntemi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="f8c47-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="f8c47-110">Birden çok parametre belgeye birden çok kullanın \<param > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="f8c47-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="f8c47-111">Metni \<param > etiketi, IntelliSense, Nesne Tarayıcısı ve kod açıklaması Web rapor görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f8c47-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="f8c47-112">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="f8c47-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8c47-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8c47-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f8c47-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8c47-114">See Also</span></span>

- [<span data-ttu-id="f8c47-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f8c47-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f8c47-116">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="f8c47-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
