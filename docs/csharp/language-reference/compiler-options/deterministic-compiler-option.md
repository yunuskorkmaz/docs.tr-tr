---
description: -belirleyici (C# derleyici seçenekleri)
title: -belirleyici (C# derleyici seçenekleri)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: 9d0bcc2957e5a666c21cdc2ce61e74fc90fe3530
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125832"
---
# <a name="-deterministic"></a><span data-ttu-id="c1ecc-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="c1ecc-103">-deterministic</span></span>

<span data-ttu-id="c1ecc-104">Derleyicinin bayt çıkışı, aynı girişlerin derlemeleri arasında özdeş olan bir derleme üretmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1ecc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1ecc-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="c1ecc-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1ecc-106">Remarks</span></span>

<span data-ttu-id="c1ecc-107">Varsayılan olarak, belirli bir giriş kümesinden Derleyici çıktısı benzersizdir, çünkü derleyici bir zaman damgası ve rastgele sayıdan oluşturulan bir GUID ekliyor.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="c1ecc-108">`-deterministic`Değer aynı kaldığı sürece, bir *belirleyici derleme*oluşturmak için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="c1ecc-109">Derleyici, belirlemeleri için aşağıdaki girişleri dikkate alır:</span><span class="sxs-lookup"><span data-stu-id="c1ecc-109">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="c1ecc-110">Komut satırı parametrelerinin sırası.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-110">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="c1ecc-111">Derleyicinin. rsp yanıt dosyasının içeriği.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-111">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="c1ecc-112">Kullanılan derleyicinin kesin sürümü ve başvurulan derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-112">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="c1ecc-113">Geçerli dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-113">The current directory path.</span></span>
- <span data-ttu-id="c1ecc-114">Açıkça derleyiciye doğrudan veya dolaylı olarak geçirilen tüm dosyaların ikili içeriği:</span><span class="sxs-lookup"><span data-stu-id="c1ecc-114">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="c1ecc-115">Kaynak dosyalar</span><span class="sxs-lookup"><span data-stu-id="c1ecc-115">Source files</span></span>
  - <span data-ttu-id="c1ecc-116">Başvurulan derlemeler</span><span class="sxs-lookup"><span data-stu-id="c1ecc-116">Referenced assemblies</span></span>
  - <span data-ttu-id="c1ecc-117">Başvurulan modüller</span><span class="sxs-lookup"><span data-stu-id="c1ecc-117">Referenced modules</span></span>
  - <span data-ttu-id="c1ecc-118">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c1ecc-118">Resources</span></span>
  - <span data-ttu-id="c1ecc-119">Tanımlayıcı ad anahtar dosyası</span><span class="sxs-lookup"><span data-stu-id="c1ecc-119">The strong name key file</span></span>
  - <span data-ttu-id="c1ecc-120">@ Yanıt dosyaları</span><span class="sxs-lookup"><span data-stu-id="c1ecc-120">@ response files</span></span>
  - <span data-ttu-id="c1ecc-121">Çözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="c1ecc-121">Analyzers</span></span>
  - <span data-ttu-id="c1ecc-122">RuleSets</span><span class="sxs-lookup"><span data-stu-id="c1ecc-122">Rulesets</span></span>
  - <span data-ttu-id="c1ecc-123">Çözümleyiciler tarafından kullanılabilecek ek dosyalar</span><span class="sxs-lookup"><span data-stu-id="c1ecc-123">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="c1ecc-124">Geçerli kültür (tanılama ve özel durum iletilerinin oluşturulduğu dil için).</span><span class="sxs-lookup"><span data-stu-id="c1ecc-124">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="c1ecc-125">Kodlama belirtilmemişse, varsayılan kodlama (veya geçerli kod sayfası).</span><span class="sxs-lookup"><span data-stu-id="c1ecc-125">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="c1ecc-126">Derleyicinin arama yollarındaki dosyaların varlığı, var olmayan ve içeriği (örneğin, `-lib` veya ile `-recurse` ).</span><span class="sxs-lookup"><span data-stu-id="c1ecc-126">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="c1ecc-127">Derleyicinin çalıştırıldığı CLR platformu.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-127">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="c1ecc-128">`%LIBPATH%`, Çözümleyici bağımlılığı yüklemeyi etkileyebilecek değeri.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-128">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="c1ecc-129">Kaynaklar herkese açık olduğunda, bir ikilinin güvenilir bir kaynaktan derlenip derlenmediğini oluşturmak için belirleyici derleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-129">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="c1ecc-130">Ayrıca, bir ikiliye yapılan değişikliklere bağımlı derleme adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir derleme sisteminde de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-130">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1ecc-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1ecc-131">See also</span></span>

- [<span data-ttu-id="c1ecc-132">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c1ecc-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c1ecc-133">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="c1ecc-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
