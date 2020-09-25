---
description: '#pragma-C# başvurusu'
title: '#pragma-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 2788c2589bee149676c5cb2b4212ec7a060a47af
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168523"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="61ec6-103">#pragma (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="61ec6-103">#pragma (C# Reference)</span></span>

<span data-ttu-id="61ec6-104">`#pragma` Derleyicinin göründüğü dosyanın derlenmesi için özel yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="61ec6-104">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="61ec6-105">Yönergeler derleyici tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="61ec6-105">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="61ec6-106">Diğer bir deyişle, `#pragma` özel ön işleme yönergeleri oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="61ec6-106">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="61ec6-107">Microsoft C# derleyicisi aşağıdaki iki `#pragma` yönergeleri destekler:</span><span class="sxs-lookup"><span data-stu-id="61ec6-107">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="61ec6-108">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="61ec6-108">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="61ec6-109">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="61ec6-109">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="61ec6-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61ec6-110">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="61ec6-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61ec6-111">Parameters</span></span>  

 `pragma-name`  
 <span data-ttu-id="61ec6-112">Tanınan bir pragma adı.</span><span class="sxs-lookup"><span data-stu-id="61ec6-112">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="61ec6-113">Pragma 'a özgü bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="61ec6-113">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ec6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61ec6-114">See also</span></span>

- [<span data-ttu-id="61ec6-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="61ec6-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="61ec6-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="61ec6-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="61ec6-117">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="61ec6-117">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="61ec6-118">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="61ec6-118">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="61ec6-119">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="61ec6-119">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
