---
title: '&lt;izin&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 815d303c9cfbf01588f5f2877e9f87a7ebbea9a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321483"
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="c5a5e-102">&lt;izin&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c5a5e-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c5a5e-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5a5e-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5a5e-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5a5e-104">Parameters</span></span>  
 <span data-ttu-id="c5a5e-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="c5a5e-105">cref = " `member`"</span></span>  
 <span data-ttu-id="c5a5e-106">Bir üye ya da geçerli derleme ortamından çağrılacak kullanılabilir alan başvuru.</span><span class="sxs-lookup"><span data-stu-id="c5a5e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="c5a5e-107">Verilen code öğesi var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="c5a5e-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="c5a5e-108">*üye* çift tırnak işaretleri içinde görünmesi gerekir ("").</span><span class="sxs-lookup"><span data-stu-id="c5a5e-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="c5a5e-109">Genel bir tür cref başvuru oluşturma hakkında daha fazla bilgi için bkz: [ \<bkz >](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="c5a5e-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="c5a5e-110">Üye erişimi açıklaması.</span><span class="sxs-lookup"><span data-stu-id="c5a5e-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5a5e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5a5e-111">Remarks</span></span>  
 <span data-ttu-id="c5a5e-112">\<İzni > etiketi üyesi erişim belge olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a5e-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="c5a5e-113"><xref:System.Security.PermissionSet> Sınıfı üyesi erişmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a5e-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="c5a5e-114">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="c5a5e-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5a5e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5a5e-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c5a5e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5a5e-116">See Also</span></span>  
 [<span data-ttu-id="c5a5e-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c5a5e-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c5a5e-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="c5a5e-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
