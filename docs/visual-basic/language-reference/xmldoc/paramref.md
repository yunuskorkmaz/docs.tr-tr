---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 85171bd8deeb5f54c4560bb8b2339107bb8d8c68
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524714"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="6e7a3-102">\<paramref > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e7a3-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="6e7a3-103">Bir sözcüğü parametre olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="6e7a3-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e7a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e7a3-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e7a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e7a3-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6e7a3-106">Başvurabileceğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="6e7a3-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="6e7a3-107">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="6e7a3-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e7a3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e7a3-108">Remarks</span></span>  
 <span data-ttu-id="6e7a3-109">@No__t_0 etiketi, bir sözcüğün bir parametre olduğunu göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a3-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="6e7a3-110">XML dosyası bu parametreyi farklı bir şekilde biçimlendirmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="6e7a3-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="6e7a3-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="6e7a3-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e7a3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e7a3-112">Example</span></span>  
 <span data-ttu-id="6e7a3-113">Bu örnek, `id` parametresine başvurmak için `<paramref>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6e7a3-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6e7a3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e7a3-114">See also</span></span>

- [<span data-ttu-id="6e7a3-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="6e7a3-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
