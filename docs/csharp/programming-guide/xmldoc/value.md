---
title: '&lt;değer&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ea900c21c2c0477c626be5eff2403312d9e8609
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="c463f-102">&lt;değer&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c463f-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c463f-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c463f-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c463f-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c463f-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="c463f-105">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="c463f-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c463f-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c463f-106">Remarks</span></span>  
 <span data-ttu-id="c463f-107">\<Değeri > etiketi bir özelliği temsil eden bir değeri açıklamak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c463f-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="c463f-108">Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, onu ekleyeceksiniz Not bir [ \<Özet >](../../../csharp/programming-guide/xmldoc/summary.md) yeni özellik için etiketi.</span><span class="sxs-lookup"><span data-stu-id="c463f-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="c463f-109">Daha sonra el ile eklemeniz bir \<değeri > özelliği temsil eden bir değeri açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="c463f-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="c463f-110">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="c463f-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c463f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c463f-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c463f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c463f-112">See Also</span></span>  
 [<span data-ttu-id="c463f-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c463f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c463f-114">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="c463f-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
