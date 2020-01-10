---
title: <permission> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 67e9d398d1bb43d480f8ca56733106e0f0a22731
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696577"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="41925-102">\<izin > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="41925-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="41925-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41925-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="41925-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41925-104">Parameters</span></span>  
 <span data-ttu-id="41925-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="41925-105">cref = " `member`"</span></span>  
 <span data-ttu-id="41925-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="41925-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="41925-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında kurallı öğe adına `member` çevirir.</span><span class="sxs-lookup"><span data-stu-id="41925-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="41925-108">*üye* çift tırnak işareti ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="41925-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="41925-109">Genel bir türe cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. [\<](./see.md).</span><span class="sxs-lookup"><span data-stu-id="41925-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="41925-110">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="41925-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41925-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41925-111">Remarks</span></span>  
 <span data-ttu-id="41925-112">\<izin > etiketi bir üyenin erişimini belgelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="41925-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="41925-113"><xref:System.Security.PermissionSet> sınıfı, bir üyeye erişim belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="41925-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="41925-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="41925-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41925-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="41925-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="41925-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41925-116">See also</span></span>

- [<span data-ttu-id="41925-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="41925-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="41925-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="41925-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
