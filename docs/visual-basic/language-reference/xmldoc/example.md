---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f28dbf19bc03cb9d91323e9fa43a7081c1990db
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524010"
---
# <a name="example-visual-basic"></a><span data-ttu-id="c7030-102">\<example > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7030-102">\<example> (Visual Basic)</span></span>
<span data-ttu-id="c7030-103">Üye için bir örnek belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7030-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7030-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7030-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7030-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7030-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c7030-106">Kod örneğinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="c7030-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7030-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7030-107">Remarks</span></span>  
 <span data-ttu-id="c7030-108">@No__t_0 etiketi, bir yöntemin veya diğer kitaplık üyesinin nasıl kullanılacağına ilişkin bir örnek belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c7030-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="c7030-109">Bu genellikle [\<code >](../../../visual-basic/language-reference/xmldoc/code.md) etiketinin kullanılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="c7030-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="c7030-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="c7030-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7030-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7030-111">Example</span></span>  
 <span data-ttu-id="c7030-112">Bu örnek, `ID` alanı kullanmak için bir örnek eklemek için `<example>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7030-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c7030-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7030-113">See also</span></span>

- [<span data-ttu-id="c7030-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="c7030-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
