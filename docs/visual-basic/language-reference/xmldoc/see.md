---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e3ae5fb63540e47e5b8da2e2d60d5bd736e019d7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524662"
---
# <a name="see-visual-basic"></a><span data-ttu-id="c3ff0-102">\<see > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3ff0-102">\<see> (Visual Basic)</span></span>
<span data-ttu-id="c3ff0-103">Başka bir üyeye bağlantı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ff0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3ff0-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3ff0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3ff0-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="c3ff0-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="c3ff0-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="c3ff0-108">`member` çift tırnak işaretleri ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3ff0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3ff0-109">Remarks</span></span>  
 <span data-ttu-id="c3ff0-110">Metnin içinden bir bağlantı belirtmek için `<see>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="c3ff0-111">Bir "Ayrıca bkz." bölümünde görünmesini isteyebileceğiniz metni göstermek için [\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="c3ff0-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3ff0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3ff0-113">Example</span></span>  
 <span data-ttu-id="c3ff0-114">Bu örnek `DoesRecordExist` yöntemine başvurmak için `UpdateRecord` açıklamaları bölümündeki `<see>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c3ff0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-115">See also</span></span>

- [<span data-ttu-id="c3ff0-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="c3ff0-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
