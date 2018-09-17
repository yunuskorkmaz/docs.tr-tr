---
title: '&lt;izni&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: bcec5d968f5d0c5400c28e772df151b164888a47
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45667865"
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="a3a85-102">&lt;izni&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3a85-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="a3a85-103">Üye için gerekli izni belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3a85-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a85-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3a85-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3a85-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3a85-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="a3a85-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="a3a85-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a3a85-107">Derleyici belirli kod öğesi var. çevirir olup olmadığını denetler ve `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="a3a85-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a3a85-108">İçine `member` tırnak işaretleri ("").</span><span class="sxs-lookup"><span data-stu-id="a3a85-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="a3a85-109">Üye erişimi açıklaması.</span><span class="sxs-lookup"><span data-stu-id="a3a85-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3a85-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3a85-110">Remarks</span></span>  
 <span data-ttu-id="a3a85-111">Kullanım `<permission>` üyenin erişim belgelemek için etiket.</span><span class="sxs-lookup"><span data-stu-id="a3a85-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="a3a85-112">Kullanım <xref:System.Security.PermissionSet> sınıfın üyesi erişimi belirtin.</span><span class="sxs-lookup"><span data-stu-id="a3a85-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="a3a85-113">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="a3a85-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3a85-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3a85-114">Example</span></span>  
 <span data-ttu-id="a3a85-115">Bu örnekte `<permission>` açıklayan için etiket <xref:System.Security.Permissions.FileIOPermission> gerektirdiği `ReadFile` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3a85-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a3a85-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3a85-116">See Also</span></span>  
 [<span data-ttu-id="a3a85-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="a3a85-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
