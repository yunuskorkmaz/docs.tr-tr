---
description: '#Nullable-C# başvurusu'
title: '#Nullable-C# başvurusu'
ms.date: 11/18/2020
f1_keywords:
- '#nullable'
helpviewer_keywords:
- '#nullable directive [C#]'
ms.openlocfilehash: 4c114a09f29769fcc824bcdabdc1d523e33f199d
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099465"
---
# <a name="nullable-c-reference"></a><span data-ttu-id="0835d-103">#nullable (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0835d-103">#nullable (C# Reference)</span></span>

<span data-ttu-id="0835d-104">`#nullable`Önişlemci yönergesi *null yapılabilir ek açıklama bağlamını* ve *null yapılabilir uyarı bağlamını* ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0835d-104">The `#nullable` preprocessor directive sets the *nullable annotation context* and *nullable warning context*.</span></span> <span data-ttu-id="0835d-105">Bu yönerge, null yapılabilir ek açıklamaların geçerli olup olmadığını ve null olabilme uyarılarının verilip verilmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="0835d-105">This directive controls whether nullable annotations have effect, and whether nullability warnings are given.</span></span> <span data-ttu-id="0835d-106">Her bağlam *devre dışı* ya da *etkin*.</span><span class="sxs-lookup"><span data-stu-id="0835d-106">Each context is either *disabled* or *enabled*.</span></span>

<span data-ttu-id="0835d-107">Her iki içerik de proje düzeyinde belirtilebilir (C# kaynak kodu dışında).</span><span class="sxs-lookup"><span data-stu-id="0835d-107">Both contexts can be specified at the project level (outside of C# source code).</span></span> <span data-ttu-id="0835d-108">`#nullable`Yönergesi ek açıklamanın ve uyarı bağlamlarını denetler ve proje düzeyi ayarlarından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="0835d-108">The `#nullable` directive controls the annotation and warning contexts and takes precedence over the project-level settings.</span></span> <span data-ttu-id="0835d-109">Bir yönerge, başka bir yönerge tarafından geçersiz kılınana kadar veya kaynak dosyanın sonuna kadar denetlediği bağlamı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0835d-109">A directive sets the context(s) it controls until another directive overrides it, or until the end of the source file.</span></span>

<span data-ttu-id="0835d-110">Yönergelerin etkisi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0835d-110">The effect of the directives is as follows:</span></span>

- <span data-ttu-id="0835d-111">`#nullable disable`: Nullable ek açıklama ve uyarı bağlamlarını *devre dışı* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0835d-111">`#nullable disable`: Sets the nullable annotation and warning contexts to *disabled*.</span></span>
- <span data-ttu-id="0835d-112">`#nullable enable`: Null yapılabilir ek açıklama ve uyarı bağlamlarını *etkin* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0835d-112">`#nullable enable`: Sets the nullable annotation and warning contexts to *enabled*.</span></span>
- <span data-ttu-id="0835d-113">`#nullable restore`: Proje ayarlarına Nullable ek açıklama ve uyarı bağlamlarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="0835d-113">`#nullable restore`: Restores the nullable annotation and warning contexts to project settings.</span></span>
- <span data-ttu-id="0835d-114">`#nullable disable annotations`: Nullable ek açıklama bağlamını *devre dışı* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0835d-114">`#nullable disable annotations`: Sets the nullable annotation context to *disabled*.</span></span>
- <span data-ttu-id="0835d-115">`#nullable enable annotations`: Null yapılabilir ek açıklama bağlamını *etkin* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0835d-115">`#nullable enable annotations`: Sets the nullable annotation context to *enabled*.</span></span>
- <span data-ttu-id="0835d-116">`#nullable restore annotations`: Null yapılabilir ek açıklama bağlamını proje ayarlarına geri yükler.</span><span class="sxs-lookup"><span data-stu-id="0835d-116">`#nullable restore annotations`: Restores the nullable annotation context to project settings.</span></span>
- <span data-ttu-id="0835d-117">`#nullable disable warnings`: Nullable uyarı bağlamını *devre dışı* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0835d-117">`#nullable disable warnings`: Sets the nullable warning context to *disabled*.</span></span>
- <span data-ttu-id="0835d-118">`#nullable enable warnings`: Null yapılabilir uyarı bağlamını *etkin* olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0835d-118">`#nullable enable warnings`: Sets the nullable warning context to *enabled*.</span></span>
- <span data-ttu-id="0835d-119">`#nullable restore warnings`: Proje ayarlarına Nullable uyarı bağlamını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="0835d-119">`#nullable restore warnings`: Restores the nullable warning context to project settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="0835d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0835d-120">See also</span></span>

- [<span data-ttu-id="0835d-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0835d-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0835d-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0835d-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0835d-123">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0835d-123">C# Preprocessor Directives</span></span>](./index.md)
