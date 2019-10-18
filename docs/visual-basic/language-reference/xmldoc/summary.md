---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 25a0b307756401bed4d4c77d3668c2af53ba8b42
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524636"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="2a925-102">\<summary > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a925-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="2a925-103">Üyenin özetini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a925-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a925-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a925-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a925-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a925-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="2a925-106">Nesnenin Özeti.</span><span class="sxs-lookup"><span data-stu-id="2a925-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a925-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a925-107">Remarks</span></span>  
 <span data-ttu-id="2a925-108">Bir tür veya tür üyesini anlatmak için `<summary>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a925-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="2a925-109">Bir tür açıklamasına ek bilgi eklemek için [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a925-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="2a925-110">@No__t_0 etiketinin metni, IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca Nesne Tarayıcısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2a925-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="2a925-111">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="2a925-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="2a925-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="2a925-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a925-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a925-113">Example</span></span>  
 <span data-ttu-id="2a925-114">Bu örnek, `ResetCounter` yöntemini ve `Counter` özelliğini anlatmak için `<summary>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a925-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2a925-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a925-115">See also</span></span>

- [<span data-ttu-id="2a925-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="2a925-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
