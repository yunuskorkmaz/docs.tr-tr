---
title: <value> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 3495a6c88d340342362d84d6ea3f12048d42b21f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982160"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="7dd74-102">\<Değer > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7dd74-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="7dd74-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7dd74-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dd74-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7dd74-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="7dd74-105">Bir özellik için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="7dd74-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dd74-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7dd74-106">Remarks</span></span>  
 <span data-ttu-id="7dd74-107">\<Değer > etiketi temsil eden bir özellik değeri tanımlamak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7dd74-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="7dd74-108">Visual Studio .NET geliştirme ortamında bir özellik kod Sihirbazı aracılığıyla eklediğinizde, bu ekleyeceksiniz Not bir [ \<Özet >](../../../csharp/programming-guide/xmldoc/summary.md) yeni bir özellik için etiket.</span><span class="sxs-lookup"><span data-stu-id="7dd74-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="7dd74-109">Daha sonra el ile eklemelisiniz bir \<değer > özelliği temsil eden bir değeri açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="7dd74-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="7dd74-110">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="7dd74-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dd74-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7dd74-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="7dd74-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd74-112">See also</span></span>

- [<span data-ttu-id="7dd74-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7dd74-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7dd74-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="7dd74-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
