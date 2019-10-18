---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0231ff748949874f4b477cac15d891d313b25f4f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524652"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="d7d8d-102">\<seealso > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7d8d-102">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="d7d8d-103">Ayrıca bkz. bölümünde görüntülenen bir bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7d8d-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7d8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7d8d-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="d7d8d-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="d7d8d-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="d7d8d-108">`member` çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7d8d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7d8d-109">Remarks</span></span>  
 <span data-ttu-id="d7d8d-110">Ayrıca bkz. bölümünde görünmesini istediğiniz metni belirtmek için `<seealso>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="d7d8d-111">Metnin içinden bir bağlantı belirtmek için [\<see >](../../../visual-basic/language-reference/xmldoc/see.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="d7d8d-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7d8d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7d8d-113">Example</span></span>  
 <span data-ttu-id="d7d8d-114">Bu örnek `UpdateRecord` yöntemine başvurmak için `DoesRecordExist` açıklamaları bölümündeki `<seealso>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="d7d8d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7d8d-115">See also</span></span>

- [<span data-ttu-id="d7d8d-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d7d8d-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
