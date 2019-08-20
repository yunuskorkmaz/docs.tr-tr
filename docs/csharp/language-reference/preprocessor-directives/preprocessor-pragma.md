---
title: '#pragma- C# Reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65ca38ff6993117b6ed9f716d4ac93ba2d4a9ddf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605662"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="1676f-102">#pragma (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1676f-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="1676f-103">`#pragma`Derleyicinin göründüğü dosyanın derlenmesi için özel yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1676f-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="1676f-104">Yönergeler derleyici tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="1676f-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="1676f-105">Diğer bir deyişle, özel ön işleme `#pragma` yönergeleri oluşturmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1676f-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="1676f-106">Microsoft C# derleyicisi aşağıdaki iki `#pragma` yönergeleri destekler:</span><span class="sxs-lookup"><span data-stu-id="1676f-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="1676f-107">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="1676f-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="1676f-108">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="1676f-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="1676f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1676f-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="1676f-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1676f-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="1676f-111">Tanınan bir pragma adı.</span><span class="sxs-lookup"><span data-stu-id="1676f-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="1676f-112">Pragma 'a özgü bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="1676f-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1676f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1676f-113">See also</span></span>

- [<span data-ttu-id="1676f-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="1676f-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1676f-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1676f-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1676f-116">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1676f-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="1676f-117">#pragma uyarısı</span><span class="sxs-lookup"><span data-stu-id="1676f-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="1676f-118">#pragma sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="1676f-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
