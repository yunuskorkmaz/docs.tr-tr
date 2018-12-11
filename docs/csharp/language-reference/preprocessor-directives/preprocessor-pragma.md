---
title: '#pragma - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65867bc441711193f93142d1c65122b6bc60c25d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241833"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="2bcc6-102">#pragma (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2bcc6-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="2bcc6-103">`#pragma` Derleyici göründüğü dosyanın derleme için özel yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bcc6-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="2bcc6-104">Yönergeleri, derleyici tarafından desteklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bcc6-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="2bcc6-105">Diğer bir deyişle, kullanamazsınız `#pragma` özel ön işleme yönergeleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="2bcc6-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="2bcc6-106">Aşağıdaki iki Microsoft C# derleyicisi destekleyen `#pragma` yönergeleri:</span><span class="sxs-lookup"><span data-stu-id="2bcc6-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="2bcc6-107">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="2bcc6-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="2bcc6-108">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="2bcc6-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="2bcc6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bcc6-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bcc6-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bcc6-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="2bcc6-111">Tanınan bir pragma adı.</span><span class="sxs-lookup"><span data-stu-id="2bcc6-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="2bcc6-112">Pragma özel bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="2bcc6-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcc6-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2bcc6-113">See Also</span></span>

- [<span data-ttu-id="2bcc6-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2bcc6-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2bcc6-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2bcc6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2bcc6-116">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2bcc6-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [<span data-ttu-id="2bcc6-117">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="2bcc6-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
- [<span data-ttu-id="2bcc6-118">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="2bcc6-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
