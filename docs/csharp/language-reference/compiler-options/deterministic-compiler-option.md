---
title: -belirleyici (C# derleyici seçenekleri)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3950578e9e5d1acb517e7d96c76454b198ba3e1c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606932"
---
# <a name="-deterministic"></a><span data-ttu-id="ba8e0-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="ba8e0-102">-deterministic</span></span>

<span data-ttu-id="ba8e0-103">Derleyicinin bayt çıkışı, aynı girişlerin derlemeleri arasında özdeş olan bir derleme üretmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba8e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba8e0-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="ba8e0-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba8e0-105">Remarks</span></span>

<span data-ttu-id="ba8e0-106">Varsayılan olarak, belirli bir giriş kümesinden Derleyici çıktısı benzersizdir, çünkü derleyici bir zaman damgası ve rastgele sayıdan oluşturulan bir GUID ekliyor.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="ba8e0-107">Değer aynı kaldığı `-deterministic` sürece, bir *belirleyici derleme*oluşturmak için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="ba8e0-108">Derleyici, belirlemeleri için aşağıdaki girişleri dikkate alır:</span><span class="sxs-lookup"><span data-stu-id="ba8e0-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="ba8e0-109">Komut satırı parametrelerinin sırası.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="ba8e0-110">Derleyicinin. rsp yanıt dosyasının içeriği.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="ba8e0-111">Kullanılan derleyicinin kesin sürümü ve başvurulan derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="ba8e0-112">Geçerli dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-112">The current directory path.</span></span>
- <span data-ttu-id="ba8e0-113">Açıkça derleyiciye doğrudan veya dolaylı olarak geçirilen tüm dosyaların ikili içeriği:</span><span class="sxs-lookup"><span data-stu-id="ba8e0-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="ba8e0-114">Kaynak dosyalar</span><span class="sxs-lookup"><span data-stu-id="ba8e0-114">Source files</span></span>
  - <span data-ttu-id="ba8e0-115">Başvurulan derlemeler</span><span class="sxs-lookup"><span data-stu-id="ba8e0-115">Referenced assemblies</span></span>
  - <span data-ttu-id="ba8e0-116">Başvurulan modüller</span><span class="sxs-lookup"><span data-stu-id="ba8e0-116">Referenced modules</span></span>
  - <span data-ttu-id="ba8e0-117">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="ba8e0-117">Resources</span></span>
  - <span data-ttu-id="ba8e0-118">Tanımlayıcı ad anahtar dosyası</span><span class="sxs-lookup"><span data-stu-id="ba8e0-118">The strong name key file</span></span>
  - <span data-ttu-id="ba8e0-119">@ Yanıt dosyaları</span><span class="sxs-lookup"><span data-stu-id="ba8e0-119">@ response files</span></span>
  - <span data-ttu-id="ba8e0-120">Çözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="ba8e0-120">Analyzers</span></span>
  - <span data-ttu-id="ba8e0-121">RuleSets</span><span class="sxs-lookup"><span data-stu-id="ba8e0-121">Rulesets</span></span>
  - <span data-ttu-id="ba8e0-122">Çözümleyiciler tarafından kullanılabilecek ek dosyalar</span><span class="sxs-lookup"><span data-stu-id="ba8e0-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="ba8e0-123">Geçerli kültür (tanılama ve özel durum iletilerinin oluşturulduğu dil için).</span><span class="sxs-lookup"><span data-stu-id="ba8e0-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="ba8e0-124">Kodlama belirtilmemişse, varsayılan kodlama (veya geçerli kod sayfası).</span><span class="sxs-lookup"><span data-stu-id="ba8e0-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="ba8e0-125">Derleyicinin arama yollarındaki dosyaların varlığı, var olmayan ve içeriği (örneğin, veya `/lib` `/recurse`ile).</span><span class="sxs-lookup"><span data-stu-id="ba8e0-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="ba8e0-126">Derleyicinin çalıştırıldığı CLR platformu.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="ba8e0-127">`%LIBPATH%`, Çözümleyici bağımlılığı yüklemeyi etkileyebilecek değeri.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="ba8e0-128">Kaynaklar herkese açık olduğunda, bir ikilinin güvenilir bir kaynaktan derlenip derlenmediğini oluşturmak için belirleyici derleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="ba8e0-129">Ayrıca, bir ikiliye yapılan değişikliklere bağımlı derleme adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir derleme sisteminde de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba8e0-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba8e0-130">See also</span></span>

- [<span data-ttu-id="ba8e0-131">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ba8e0-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ba8e0-132">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="ba8e0-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
