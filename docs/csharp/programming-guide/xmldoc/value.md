---
title: '&lt;değer&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 24ef4aba13668cd04e20f17ebffac9eb68e796ca
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561634"
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="2ec53-102">&lt;değer&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2ec53-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="2ec53-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ec53-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ec53-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ec53-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="2ec53-105">Bir özellik için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="2ec53-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec53-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ec53-106">Remarks</span></span>  
 <span data-ttu-id="2ec53-107">\<Değer > etiketi temsil eden bir özellik değeri tanımlamak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="2ec53-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="2ec53-108">Visual Studio .NET geliştirme ortamında bir özellik kod Sihirbazı aracılığıyla eklediğinizde, bu ekleyeceksiniz Not bir [ \<Özet >](../../../csharp/programming-guide/xmldoc/summary.md) yeni bir özellik için etiket.</span><span class="sxs-lookup"><span data-stu-id="2ec53-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="2ec53-109">Daha sonra el ile eklemelisiniz bir \<değer > özelliği temsil eden bir değeri açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="2ec53-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="2ec53-110">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="2ec53-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ec53-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ec53-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2ec53-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ec53-112">See Also</span></span>

- [<span data-ttu-id="2ec53-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2ec53-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2ec53-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="2ec53-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
