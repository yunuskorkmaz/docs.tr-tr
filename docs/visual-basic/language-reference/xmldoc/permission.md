---
title: '&lt;izin&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 67e11998e43a43f92c26eb5f7daa488d288823c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="9e27f-102">&lt;izin&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e27f-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="9e27f-103">Üye için gerekli izni belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e27f-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e27f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e27f-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e27f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e27f-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="9e27f-106">Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="9e27f-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="9e27f-107">Verilen code öğesi var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="9e27f-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="9e27f-108">İçine `member` tırnak işaretleri ("").</span><span class="sxs-lookup"><span data-stu-id="9e27f-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="9e27f-109">Üye erişimi açıklaması.</span><span class="sxs-lookup"><span data-stu-id="9e27f-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e27f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e27f-110">Remarks</span></span>  
 <span data-ttu-id="9e27f-111">Kullanım `<permission>` üyesi erişim belge etiketi.</span><span class="sxs-lookup"><span data-stu-id="9e27f-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="9e27f-112">Kullanım <xref:System.Security.PermissionSet> üyesi için erişimi belirtmek üzere sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9e27f-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="9e27f-113">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="9e27f-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e27f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e27f-114">Example</span></span>  
 <span data-ttu-id="9e27f-115">Bu örnekte `<permission>` açıklayan etiketi <xref:System.Security.Permissions.FileIOPermission> gerekli `ReadFile` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9e27f-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9e27f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e27f-116">See Also</span></span>  
 [<span data-ttu-id="9e27f-117">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="9e27f-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
