---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 71b00b669804e644d1171480192b9d55455bdf53
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352271"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="3cac9-101">\<izin > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cac9-101">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="3cac9-102">Üye için gerekli izinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3cac9-102">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cac9-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cac9-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cac9-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cac9-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="3cac9-105">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="3cac9-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="3cac9-106">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir.</span><span class="sxs-lookup"><span data-stu-id="3cac9-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="3cac9-107">`member` tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="3cac9-107">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="3cac9-108">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="3cac9-108">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cac9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cac9-109">Remarks</span></span>  
 <span data-ttu-id="3cac9-110">Üyenin erişimini belgelemek için `<permission>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3cac9-110">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="3cac9-111">Bir üyeye erişimi belirtmek için <xref:System.Security.PermissionSet> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="3cac9-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="3cac9-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="3cac9-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cac9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3cac9-113">Example</span></span>  
 <span data-ttu-id="3cac9-114">Bu örnek, `ReadFile` yöntemi tarafından <xref:System.Security.Permissions.FileIOPermission> gerektiğini belirtmek için `<permission>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3cac9-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="3cac9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cac9-115">See also</span></span>

- [<span data-ttu-id="3cac9-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="3cac9-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
