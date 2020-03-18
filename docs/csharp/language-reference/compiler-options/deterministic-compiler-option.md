---
title: -deterministic (C# Derleyici Seçenekleri)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: ed5d1db4618649391f88affad67e62dd9fc95925
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73455177"
---
# <a name="-deterministic"></a><span data-ttu-id="45e9e-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="45e9e-102">-deterministic</span></span>

<span data-ttu-id="45e9e-103">Derleyicinin, bayt için bayt çıktısı aynı girişler için derlemeler arasında aynı olan bir derleme oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="45e9e-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="45e9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45e9e-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="45e9e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45e9e-105">Remarks</span></span>

<span data-ttu-id="45e9e-106">Derleyici rasgele sayılardan oluşturulan bir zaman damgası ve GUID eklediğiiçin, varsayılan olarak, belirli bir giriş kümesinden derleyici çıktısı benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="45e9e-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="45e9e-107">Giriş aynı `-deterministic` kaldığı sürece ikili içeriği derlemeler arasında aynı olan *deterministik*bir derleme oluşturmak için bu seçeneği kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="45e9e-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="45e9e-108">Derleyici determinizm amacıyla aşağıdaki girdileri dikkate alır:</span><span class="sxs-lookup"><span data-stu-id="45e9e-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="45e9e-109">Komut satırı parametrelerinin sırası.</span><span class="sxs-lookup"><span data-stu-id="45e9e-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="45e9e-110">Derleyicinin .rsp yanıt dosyasının içeriği.</span><span class="sxs-lookup"><span data-stu-id="45e9e-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="45e9e-111">Derleyicinin kullanılan kesin sürümü ve başvurulan derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="45e9e-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="45e9e-112">Geçerli dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="45e9e-112">The current directory path.</span></span>
- <span data-ttu-id="45e9e-113">Aşağıdakiler dahil olmak üzere, tüm dosyaların ikili içeriği doğrudan veya dolaylı olarak derleyiciye açıkça iletilir:</span><span class="sxs-lookup"><span data-stu-id="45e9e-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="45e9e-114">Kaynak dosyaları</span><span class="sxs-lookup"><span data-stu-id="45e9e-114">Source files</span></span>
  - <span data-ttu-id="45e9e-115">Başvurulan derlemeler</span><span class="sxs-lookup"><span data-stu-id="45e9e-115">Referenced assemblies</span></span>
  - <span data-ttu-id="45e9e-116">Başvurulan modüller</span><span class="sxs-lookup"><span data-stu-id="45e9e-116">Referenced modules</span></span>
  - <span data-ttu-id="45e9e-117">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="45e9e-117">Resources</span></span>
  - <span data-ttu-id="45e9e-118">Güçlü ad anahtarı dosyası</span><span class="sxs-lookup"><span data-stu-id="45e9e-118">The strong name key file</span></span>
  - <span data-ttu-id="45e9e-119">@ yanıt dosyaları</span><span class="sxs-lookup"><span data-stu-id="45e9e-119">@ response files</span></span>
  - <span data-ttu-id="45e9e-120">Çözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="45e9e-120">Analyzers</span></span>
  - <span data-ttu-id="45e9e-121">Kural kümeleri</span><span class="sxs-lookup"><span data-stu-id="45e9e-121">Rulesets</span></span>
  - <span data-ttu-id="45e9e-122">Çözümleyiciler tarafından kullanılabilecek ek dosyalar</span><span class="sxs-lookup"><span data-stu-id="45e9e-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="45e9e-123">Geçerli kültür (tanılama ve özel durum iletilerinin üretildiği dil için).</span><span class="sxs-lookup"><span data-stu-id="45e9e-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="45e9e-124">Kodlama belirtilmemişse varsayılan kodlama (veya geçerli kod sayfası).</span><span class="sxs-lookup"><span data-stu-id="45e9e-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="45e9e-125">Derleyicinin arama yollarında dosyaların varlığı, varlığı ve içeriği (örneğin, tarafından `-lib` veya `-recurse`tarafından belirtilir).</span><span class="sxs-lookup"><span data-stu-id="45e9e-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="45e9e-126">Derleyicinin çalıştırıldığı CLR platformu.</span><span class="sxs-lookup"><span data-stu-id="45e9e-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="45e9e-127">Çözümleyici `%LIBPATH%`bağımlılık yüklemesini etkileyebilecek değeri.</span><span class="sxs-lookup"><span data-stu-id="45e9e-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="45e9e-128">Kaynaklar genel kullanıma sunulduğunda, ikilinin güvenilir bir kaynaktan derlenip derlenmediğini belirlemek için deterministik derleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45e9e-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="45e9e-129">Ayrıca, ikili gereksinimdeki değişikliklere bağlı olan yapı adımlarının yürütülmesi gerekip gerekmediğini belirlemek için sürekli bir yapı sisteminde de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="45e9e-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="45e9e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45e9e-130">See also</span></span>

- [<span data-ttu-id="45e9e-131">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="45e9e-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="45e9e-132">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="45e9e-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
