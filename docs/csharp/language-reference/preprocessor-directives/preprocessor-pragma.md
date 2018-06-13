---
title: '#pragma (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: a4829d5062474922d45a2f4f8e1cddf9023b6ad8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278815"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="14e3b-102">#pragma (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="14e3b-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="14e3b-103">`#pragma` Derleyici göründüğü dosyası derleme için özel yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="14e3b-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="14e3b-104">Yönergeleri derleyici tarafından desteklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="14e3b-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="14e3b-105">Diğer bir deyişle, kullanamazsınız `#pragma` özel önişlem yönergelerini oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="14e3b-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="14e3b-106">Aşağıdaki iki Microsoft C# Derleyici destekleyen `#pragma` yönergeler:</span><span class="sxs-lookup"><span data-stu-id="14e3b-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="14e3b-107">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="14e3b-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="14e3b-108">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="14e3b-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="14e3b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14e3b-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14e3b-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14e3b-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="14e3b-111">Bir tanınan pragma adı.</span><span class="sxs-lookup"><span data-stu-id="14e3b-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="14e3b-112">Pragma özgü bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="14e3b-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e3b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14e3b-113">See Also</span></span>  
 [<span data-ttu-id="14e3b-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="14e3b-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="14e3b-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="14e3b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="14e3b-116">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="14e3b-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="14e3b-117">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="14e3b-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="14e3b-118">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="14e3b-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
