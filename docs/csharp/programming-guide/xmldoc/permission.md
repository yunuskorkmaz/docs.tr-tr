---
title: '&lt;izni&gt; - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 5d78261807ab06bd5f89b5438648c5eb0dc56ad9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739465"
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="f5cd3-102">&lt;izni&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f5cd3-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="f5cd3-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5cd3-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5cd3-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5cd3-104">Parameters</span></span>  
 <span data-ttu-id="f5cd3-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="f5cd3-105">cref = " `member`"</span></span>  
 <span data-ttu-id="f5cd3-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="f5cd3-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f5cd3-107">Derleyici belirli kod öğesi var. çevirir olup olmadığını denetler ve `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="f5cd3-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="f5cd3-108">*üye* çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="f5cd3-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="f5cd3-109">Genel tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bakın >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="f5cd3-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="f5cd3-110">Üye erişimi açıklaması.</span><span class="sxs-lookup"><span data-stu-id="f5cd3-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5cd3-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5cd3-111">Remarks</span></span>  
 <span data-ttu-id="f5cd3-112">\<İzni > etiketi üyenin erişim belge olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f5cd3-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="f5cd3-113"><xref:System.Security.PermissionSet> Sınıf üyesi erişimi belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5cd3-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="f5cd3-114">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="f5cd3-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5cd3-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5cd3-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f5cd3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5cd3-116">See also</span></span>

- [<span data-ttu-id="f5cd3-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f5cd3-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f5cd3-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="f5cd3-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
