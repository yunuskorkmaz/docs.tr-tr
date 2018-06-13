---
title: '&lt;değer&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 22de15560d6db6e8a70cea744dd9d85359336306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356437"
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="3b8ed-102">&lt;değer&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3b8ed-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="3b8ed-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b8ed-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b8ed-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b8ed-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="3b8ed-105">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="3b8ed-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b8ed-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b8ed-106">Remarks</span></span>  
 <span data-ttu-id="3b8ed-107">\<Değeri > etiketi bir özelliği temsil eden bir değeri açıklamak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b8ed-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="3b8ed-108">Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, onu ekleyeceksiniz Not bir [ \<Özet >](../../../csharp/programming-guide/xmldoc/summary.md) yeni özellik için etiketi.</span><span class="sxs-lookup"><span data-stu-id="3b8ed-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="3b8ed-109">Daha sonra el ile eklemeniz bir \<değeri > özelliği temsil eden bir değeri açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="3b8ed-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="3b8ed-110">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="3b8ed-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b8ed-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b8ed-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3b8ed-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b8ed-112">See Also</span></span>  
 [<span data-ttu-id="3b8ed-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3b8ed-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3b8ed-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="3b8ed-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
