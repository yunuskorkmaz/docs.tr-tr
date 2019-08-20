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
ms.openlocfilehash: 4d967d671b3a27698b457c80ff5a8f7031dc6bcb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587416"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="b5970-102">\<değer > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b5970-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b5970-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5970-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5970-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5970-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="b5970-105">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="b5970-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5970-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5970-106">Remarks</span></span>  
 <span data-ttu-id="b5970-107">> \<Tag değeri, bir özelliğin temsil ettiği değeri açıklamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5970-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="b5970-108">Visual Studio .NET geliştirme ortamında kod Sihirbazı aracılığıyla bir özellik eklediğinizde, yeni özellik için bir [ \<Özet >](./summary.md) etiketi ekleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b5970-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="b5970-109">Daha sonra özelliğin temsil ettiği değeri \<tanımlayacak bir değer > etiketi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5970-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="b5970-110">Belge açıklamalarını bir dosyaya işlemek için [/doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="b5970-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5970-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5970-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="b5970-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5970-112">See also</span></span>

- [<span data-ttu-id="b5970-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b5970-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b5970-114">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="b5970-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
