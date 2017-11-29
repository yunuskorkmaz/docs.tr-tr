---
title: "#<a name=\"pragma-c-reference\"></a>pragma (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma'
helpviewer_keywords: '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f53bd0ed3f35f049b0a1cbb21c5b9a563f9fce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-c-reference"></a><span data-ttu-id="aa90e-102">#pragma (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="aa90e-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="aa90e-103">`#pragma`Derleyici göründüğü dosyası derleme için özel yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa90e-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="aa90e-104">Yönergeleri derleyici tarafından desteklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa90e-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="aa90e-105">Diğer bir deyişle, kullanamazsınız `#pragma` özel önişlem yönergelerini oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="aa90e-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="aa90e-106">Aşağıdaki iki Microsoft C# Derleyici destekleyen `#pragma` yönergeler:</span><span class="sxs-lookup"><span data-stu-id="aa90e-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="aa90e-107">#pragma Uyarısı</span><span class="sxs-lookup"><span data-stu-id="aa90e-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="aa90e-108">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="aa90e-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="aa90e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa90e-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa90e-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa90e-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="aa90e-111">Bir tanınan pragma adı.</span><span class="sxs-lookup"><span data-stu-id="aa90e-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="aa90e-112">Pragma özgü bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="aa90e-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa90e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa90e-113">See Also</span></span>  
 [<span data-ttu-id="aa90e-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa90e-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aa90e-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa90e-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aa90e-116">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="aa90e-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="aa90e-117">#pragma Uyarısı</span><span class="sxs-lookup"><span data-stu-id="aa90e-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="aa90e-118">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="aa90e-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
