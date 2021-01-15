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
ms.openlocfilehash: d64f4d4b0d4e9b5ed2cc1ee40662dc669fc6660d
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235332"
---
# <a name="-deterministic"></a><span data-ttu-id="6d2dc-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="6d2dc-103">-deterministic</span></span>

<span data-ttu-id="6d2dc-104">Derleyicinin bayt çıkışı, aynı girişlerin derlemeleri arasında özdeş olan bir derleme üretmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="6d2dc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d2dc-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="6d2dc-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d2dc-106">Remarks</span></span>

<span data-ttu-id="6d2dc-107">Varsayılan olarak, belirli bir giriş kümesinden Derleyici çıktısı benzersizdir, çünkü derleyici bir zaman damgası ve rastgele sayıdan oluşturulan bir MVıD ekliyor.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a MVID that is generated from random numbers.</span></span> <span data-ttu-id="6d2dc-108">`-deterministic`Değer aynı kaldığı sürece, bir *belirleyici derleme* oluşturmak için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span> <span data-ttu-id="6d2dc-109">Böyle bir derlemede, zaman damgası ve MVıD alanları, tüm derleme girişlerinin bir karmasından türetilen değerlerle birlikte değişir.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-109">In such a build, the timestamp and MVID fields will be replaced with values derived from a hash of all the compilation inputs.</span></span>

<span data-ttu-id="6d2dc-110">Derleyici, belirlemeleri için aşağıdaki girişleri dikkate alır:</span><span class="sxs-lookup"><span data-stu-id="6d2dc-110">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="6d2dc-111">Komut satırı parametrelerinin sırası.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-111">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="6d2dc-112">Derleyicinin. rsp yanıt dosyasının içeriği.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-112">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="6d2dc-113">Kullanılan derleyicinin kesin sürümü ve başvurulan derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-113">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="6d2dc-114">Geçerli dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-114">The current directory path.</span></span>
- <span data-ttu-id="6d2dc-115">Açıkça derleyiciye doğrudan veya dolaylı olarak geçirilen tüm dosyaların ikili içeriği:</span><span class="sxs-lookup"><span data-stu-id="6d2dc-115">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="6d2dc-116">Kaynak dosyalar</span><span class="sxs-lookup"><span data-stu-id="6d2dc-116">Source files</span></span>
  - <span data-ttu-id="6d2dc-117">Başvurulan derlemeler</span><span class="sxs-lookup"><span data-stu-id="6d2dc-117">Referenced assemblies</span></span>
  - <span data-ttu-id="6d2dc-118">Başvurulan modüller</span><span class="sxs-lookup"><span data-stu-id="6d2dc-118">Referenced modules</span></span>
  - <span data-ttu-id="6d2dc-119">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6d2dc-119">Resources</span></span>
  - <span data-ttu-id="6d2dc-120">Tanımlayıcı ad anahtar dosyası</span><span class="sxs-lookup"><span data-stu-id="6d2dc-120">The strong name key file</span></span>
  - <span data-ttu-id="6d2dc-121">@ Yanıt dosyaları</span><span class="sxs-lookup"><span data-stu-id="6d2dc-121">@ response files</span></span>
  - <span data-ttu-id="6d2dc-122">Çözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="6d2dc-122">Analyzers</span></span>
  - <span data-ttu-id="6d2dc-123">RuleSets</span><span class="sxs-lookup"><span data-stu-id="6d2dc-123">Rulesets</span></span>
  - <span data-ttu-id="6d2dc-124">Çözümleyiciler tarafından kullanılabilecek ek dosyalar</span><span class="sxs-lookup"><span data-stu-id="6d2dc-124">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="6d2dc-125">Geçerli kültür (tanılama ve özel durum iletilerinin oluşturulduğu dil için).</span><span class="sxs-lookup"><span data-stu-id="6d2dc-125">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="6d2dc-126">Kodlama belirtilmemişse, varsayılan kodlama (veya geçerli kod sayfası).</span><span class="sxs-lookup"><span data-stu-id="6d2dc-126">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="6d2dc-127">Derleyicinin arama yollarındaki dosyaların varlığı, var olmayan ve içeriği (örneğin, `-lib` veya ile `-recurse` ).</span><span class="sxs-lookup"><span data-stu-id="6d2dc-127">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="6d2dc-128">Derleyicinin çalıştırıldığı CLR platformu.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-128">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="6d2dc-129">`%LIBPATH%`, Çözümleyici bağımlılığı yüklemeyi etkileyebilecek değeri.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-129">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="6d2dc-130">Kaynaklar herkese açık olduğunda, bir ikilinin güvenilir bir kaynaktan derlenip derlenmediğini oluşturmak için belirleyici derleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-130">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="6d2dc-131">Ayrıca, bir ikiliye yapılan değişikliklere bağımlı derleme adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir derleme sisteminde de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-131">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d2dc-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d2dc-132">See also</span></span>

- [<span data-ttu-id="6d2dc-133">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6d2dc-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6d2dc-134">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6d2dc-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
