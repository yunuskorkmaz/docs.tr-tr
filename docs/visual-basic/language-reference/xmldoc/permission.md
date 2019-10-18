---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 904d573514bf35b773d47321b7fd3b6a86e90262
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524692"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="a0786-102">\<permission > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0786-102">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="a0786-103">Üye için gerekli izinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0786-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0786-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0786-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0786-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0786-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="a0786-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="a0786-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a0786-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir.</span><span class="sxs-lookup"><span data-stu-id="a0786-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a0786-108">@No__t_0 tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="a0786-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="a0786-109">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="a0786-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0786-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0786-110">Remarks</span></span>  
 <span data-ttu-id="a0786-111">Üyenin erişimini belgelemek için `<permission>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0786-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="a0786-112">Bir üyeye erişimi belirtmek için <xref:System.Security.PermissionSet> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0786-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="a0786-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="a0786-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0786-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0786-114">Example</span></span>  
 <span data-ttu-id="a0786-115">Bu örnek, `ReadFile` yöntemi tarafından <xref:System.Security.Permissions.FileIOPermission> gerektiğini belirtmek için `<permission>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0786-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a0786-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0786-116">See also</span></span>

- [<span data-ttu-id="a0786-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="a0786-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
