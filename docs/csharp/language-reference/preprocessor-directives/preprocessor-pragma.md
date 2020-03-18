---
title: '#pragma - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712461"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="f2ba7-102">#pragma (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f2ba7-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="f2ba7-103">`#pragma`göründüğü dosyanın derleyicisi için özel talimatlar verir.</span><span class="sxs-lookup"><span data-stu-id="f2ba7-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="f2ba7-104">Yönergeler derleyici tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f2ba7-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="f2ba7-105">Başka bir deyişle, `#pragma` özel ön işleme yönergeleri oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f2ba7-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="f2ba7-106">Microsoft C# derleyicisi `#pragma` aşağıdaki iki yönergeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="f2ba7-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="f2ba7-107">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="f2ba7-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="f2ba7-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="f2ba7-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="f2ba7-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2ba7-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2ba7-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2ba7-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="f2ba7-111">Tanınan bir pragmanın adı.</span><span class="sxs-lookup"><span data-stu-id="f2ba7-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="f2ba7-112">Pragma'ya özgü argümanlar.</span><span class="sxs-lookup"><span data-stu-id="f2ba7-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ba7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2ba7-113">See also</span></span>

- [<span data-ttu-id="f2ba7-114">C# Referans</span><span class="sxs-lookup"><span data-stu-id="f2ba7-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2ba7-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f2ba7-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f2ba7-116">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="f2ba7-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="f2ba7-117">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="f2ba7-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="f2ba7-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="f2ba7-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
