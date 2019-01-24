---
title: '#pragma - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 216adebae8a498ef2f4263f46f8ccd7a20d9202f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622383"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="963c8-102">#pragma (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="963c8-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="963c8-103">`#pragma` Derleyici göründüğü dosyanın derleme için özel yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="963c8-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="963c8-104">Yönergeleri, derleyici tarafından desteklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="963c8-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="963c8-105">Diğer bir deyişle, kullanamazsınız `#pragma` özel ön işleme yönergeleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="963c8-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="963c8-106">Aşağıdaki iki Microsoft C# derleyicisi destekleyen `#pragma` yönergeleri:</span><span class="sxs-lookup"><span data-stu-id="963c8-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="963c8-107">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="963c8-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="963c8-108">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="963c8-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="963c8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="963c8-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="963c8-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="963c8-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="963c8-111">Tanınan bir pragma adı.</span><span class="sxs-lookup"><span data-stu-id="963c8-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="963c8-112">Pragma özel bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="963c8-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963c8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="963c8-113">See also</span></span>

- [<span data-ttu-id="963c8-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="963c8-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="963c8-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="963c8-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="963c8-116">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="963c8-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
- [<span data-ttu-id="963c8-117">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="963c8-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="963c8-118">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="963c8-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
