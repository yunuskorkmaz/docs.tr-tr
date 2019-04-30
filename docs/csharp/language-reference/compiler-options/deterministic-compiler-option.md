---
title: -belirleyici (C# Derleyici Seçenekleri)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c6d0c7128becb154955664cfdcf96d020de9369
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662939"
---
# <a name="-deterministic"></a><span data-ttu-id="0126c-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="0126c-102">-deterministic</span></span>

<span data-ttu-id="0126c-103">Bayt için çıktısı, aynı girişleri için derlemeler arasında özdeş bir derleme oluşturmak derleyicinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="0126c-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="0126c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0126c-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="0126c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0126c-105">Remarks</span></span>

<span data-ttu-id="0126c-106">Derleyici bir zaman damgası ve rastgele sayı oluşturulan bir GUID ekler olduğundan varsayılan olarak, belirli bir giriş kümesini derleyici çıktısını benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="0126c-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="0126c-107">Kullandığınız `-deterministic` üretmek için seçeneği bir *belirlenimci derlemeyi*, bir giriş aynı kaldığı sürece ikili içeriğe sahip derlemeler arasında aynı.</span><span class="sxs-lookup"><span data-stu-id="0126c-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="0126c-108">Derleyici, aşağıdaki girişleri gerekircilik amacıyla göz önünde bulundurur:</span><span class="sxs-lookup"><span data-stu-id="0126c-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="0126c-109">Komut satırı parametreleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="0126c-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="0126c-110">Derleyicinin .rsp yanıt dosyasının içeriği.</span><span class="sxs-lookup"><span data-stu-id="0126c-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="0126c-111">Kullanılan derleme kesin sürümünü ve onun başvurulmuş derlemeler.</span><span class="sxs-lookup"><span data-stu-id="0126c-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="0126c-112">Geçerli dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="0126c-112">The current directory path.</span></span>
- <span data-ttu-id="0126c-113">Tüm dosyaları ikili içeriğini açıkça derleyici doğrudan veya dolaylı olarak dahil olmak üzere geçirilen:</span><span class="sxs-lookup"><span data-stu-id="0126c-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="0126c-114">Kaynak dosyaları</span><span class="sxs-lookup"><span data-stu-id="0126c-114">Source files</span></span>
  - <span data-ttu-id="0126c-115">Başvurulan derlemeler</span><span class="sxs-lookup"><span data-stu-id="0126c-115">Referenced assemblies</span></span>
  - <span data-ttu-id="0126c-116">Başvurulan modül</span><span class="sxs-lookup"><span data-stu-id="0126c-116">Referenced modules</span></span>
  - <span data-ttu-id="0126c-117">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0126c-117">Resources</span></span>
  - <span data-ttu-id="0126c-118">Tanımlayıcı ad anahtar dosyası</span><span class="sxs-lookup"><span data-stu-id="0126c-118">The strong name key file</span></span>
  - <span data-ttu-id="0126c-119">@ yanıt dosyaları</span><span class="sxs-lookup"><span data-stu-id="0126c-119">@ response files</span></span>
  - <span data-ttu-id="0126c-120">Çözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="0126c-120">Analyzers</span></span>
  - <span data-ttu-id="0126c-121">Rulesets</span><span class="sxs-lookup"><span data-stu-id="0126c-121">Rulesets</span></span>
  - <span data-ttu-id="0126c-122">Çözümleyiciler tarafından kullanılan ek dosyalar</span><span class="sxs-lookup"><span data-stu-id="0126c-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="0126c-123">Geçerli kültür (hangi tanılama ve özel durum iletileri üretilir dilin).</span><span class="sxs-lookup"><span data-stu-id="0126c-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="0126c-124">Varsayılan kodlama (veya mevcut kod sayfasında) kodlama belirtilmezse.</span><span class="sxs-lookup"><span data-stu-id="0126c-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="0126c-125">Varlığı, var olmayan ve derleyicinin arama yolları dosya içeriklerini (örneğin, tarafından belirtilen `/lib` veya `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="0126c-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="0126c-126">Derleyici çalıştığı CLR platform.</span><span class="sxs-lookup"><span data-stu-id="0126c-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="0126c-127">Değerini `%LIBPATH%`, çözümleyici bağımlılık yükleniyor etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="0126c-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="0126c-128">Kaynakları genel kullanıma açık olduğunda, belirlenimci derlemeyi güvenilir bir kaynaktan bir ikili derlenmiş olup olmadığını kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0126c-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="0126c-129">Ayrıca bir ikili değişiklikleri bağımlı derleme adımları yürütülecek gerekip gerekmediğini belirlemek için bir sürekli derleme sistemi de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0126c-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0126c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0126c-130">See also</span></span>

- [<span data-ttu-id="0126c-131">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0126c-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="0126c-132">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="0126c-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
