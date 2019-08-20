---
title: <permission> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: e9eb50394f01072a194d3f746577707f89ba65dd
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587888"
---
# <a name="permission-c-programming-guide"></a><span data-ttu-id="3a43d-102">\<izin > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3a43d-102">\<permission> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="3a43d-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a43d-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a43d-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a43d-104">Parameters</span></span>  
 <span data-ttu-id="3a43d-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="3a43d-105">cref = " `member`"</span></span>  
 <span data-ttu-id="3a43d-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="3a43d-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="3a43d-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında `member` kurallı öğe adına çevirir.</span><span class="sxs-lookup"><span data-stu-id="3a43d-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="3a43d-108">*üye* çift tırnak işareti ("") içinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a43d-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="3a43d-109">Genel bir türe [ \<](./see.md)cref başvurusu oluşturma hakkında daha fazla bilgi için bkz. >.</span><span class="sxs-lookup"><span data-stu-id="3a43d-109">For information on how to create a cref reference to a generic type, see [\<see>](./see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="3a43d-110">Üyeye erişim açıklaması.</span><span class="sxs-lookup"><span data-stu-id="3a43d-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a43d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a43d-111">Remarks</span></span>  
 <span data-ttu-id="3a43d-112">\<İzin > etiketi bir üyenin erişimini belgelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a43d-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="3a43d-113">Sınıfı <xref:System.Security.PermissionSet> , bir üyeye erişim belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a43d-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="3a43d-114">Belge açıklamalarını bir dosyaya işlemek için [/doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="3a43d-114">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a43d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a43d-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="3a43d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a43d-116">See also</span></span>

- [<span data-ttu-id="3a43d-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3a43d-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3a43d-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="3a43d-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
