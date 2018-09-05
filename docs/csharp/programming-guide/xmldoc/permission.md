---
title: '&lt;izni&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 1447541f7e093a7cf434702368bdce0d07c4908b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558595"
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="a5608-102">&lt;izni&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a5608-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a5608-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5608-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5608-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5608-104">Parameters</span></span>  
 <span data-ttu-id="a5608-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="a5608-105">cref = " `member`"</span></span>  
 <span data-ttu-id="a5608-106">Bir üye veya geçerli derleme ortamdan çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="a5608-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a5608-107">Derleyici belirli kod öğesi var. çevirir olup olmadığını denetler ve `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="a5608-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a5608-108">*üye* çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="a5608-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="a5608-109">Genel tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bakın >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="a5608-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="a5608-110">Üye erişimi açıklaması.</span><span class="sxs-lookup"><span data-stu-id="a5608-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5608-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5608-111">Remarks</span></span>  
 <span data-ttu-id="a5608-112">\<İzni > etiketi üyenin erişim belge olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a5608-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="a5608-113"><xref:System.Security.PermissionSet> Sınıf üyesi erişimi belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5608-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="a5608-114">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="a5608-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5608-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5608-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a5608-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5608-116">See Also</span></span>

- [<span data-ttu-id="a5608-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a5608-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a5608-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="a5608-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
