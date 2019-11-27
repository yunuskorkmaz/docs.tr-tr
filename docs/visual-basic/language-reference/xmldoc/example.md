---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f36ac1337dd0d1400180fbd3deae2bb24ad9c58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348489"
---
# <a name="example-visual-basic"></a><span data-ttu-id="d9645-101">\<örnek > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9645-101">\<example> (Visual Basic)</span></span>
<span data-ttu-id="d9645-102">Üye için bir örnek belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9645-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9645-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9645-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9645-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9645-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="d9645-105">Kod örneğinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="d9645-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9645-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9645-106">Remarks</span></span>  
 <span data-ttu-id="d9645-107">`<example>` etiketi, bir yöntemin veya diğer kitaplık üyesinin nasıl kullanılacağına ilişkin bir örnek belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d9645-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="d9645-108">Bu genellikle [\<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) etiketinin kullanılmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="d9645-108">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="d9645-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="d9645-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9645-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9645-110">Example</span></span>  
 <span data-ttu-id="d9645-111">Bu örnek, `ID` alanı kullanmak için bir örnek eklemek için `<example>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d9645-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d9645-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9645-112">See also</span></span>

- [<span data-ttu-id="d9645-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d9645-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
