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
ms.openlocfilehash: a2cb45ea6ed5c5795c910b2f6c3575b12f8189cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213918"
---
# <a name="-deterministic"></a><span data-ttu-id="55e22-102">-belirleyici</span><span class="sxs-lookup"><span data-stu-id="55e22-102">-deterministic</span></span>

<span data-ttu-id="55e22-103">Bayt için bayt çıktısı, aynı girişleri için derlemeleri arasında aynı olan bir derleme üretmek derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="55e22-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="55e22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55e22-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="55e22-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55e22-105">Remarks</span></span>

<span data-ttu-id="55e22-106">Bir zaman damgası ve rastgele sayı oluşturulmuş bir GUID derleyici ekler beri varsayılan olarak, belirli bir giriş kümesini Derleyici çıktısı benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="55e22-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="55e22-107">Kullandığınız `-deterministic` üretmek için seçeneği bir *belirleyici derleme*, bir giriş aynı kaldığı sürece ikili içerikleri derlemeleri arasında aynı olan.</span><span class="sxs-lookup"><span data-stu-id="55e22-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="55e22-108">Derleyici determinism amacıyla aşağıdaki girişleri göz önünde bulundurur:</span><span class="sxs-lookup"><span data-stu-id="55e22-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="55e22-109">Komut satırı parametreleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="55e22-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="55e22-110">Derleyicinin .rsp yanıt dosyasının içeriği.</span><span class="sxs-lookup"><span data-stu-id="55e22-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="55e22-111">Kullanılan derleyici'nın tam sürümünü ve başvurulan derlemeler.</span><span class="sxs-lookup"><span data-stu-id="55e22-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="55e22-112">Geçerli dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="55e22-112">The current directory path.</span></span>
- <span data-ttu-id="55e22-113">Tüm dosyalar ikili içeriğini açıkça derleyiciye doğrudan veya dolaylı olarak dahil olmak üzere geçirildi:</span><span class="sxs-lookup"><span data-stu-id="55e22-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
    - <span data-ttu-id="55e22-114">Kaynak dosyaları</span><span class="sxs-lookup"><span data-stu-id="55e22-114">Source files</span></span>
    - <span data-ttu-id="55e22-115">Başvurulan derlemeler</span><span class="sxs-lookup"><span data-stu-id="55e22-115">Referenced assemblies</span></span>
    - <span data-ttu-id="55e22-116">Başvurulan modül</span><span class="sxs-lookup"><span data-stu-id="55e22-116">Referenced modules</span></span>
    - <span data-ttu-id="55e22-117">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="55e22-117">Resources</span></span>
    - <span data-ttu-id="55e22-118">Güçlü ad anahtar dosyası</span><span class="sxs-lookup"><span data-stu-id="55e22-118">The strong name key file</span></span>
    - <span data-ttu-id="55e22-119">@ yanıt dosyaları</span><span class="sxs-lookup"><span data-stu-id="55e22-119">@ response files</span></span>
    - <span data-ttu-id="55e22-120">Çözümleyiciler</span><span class="sxs-lookup"><span data-stu-id="55e22-120">Analyzers</span></span>
    - <span data-ttu-id="55e22-121">Rulesets</span><span class="sxs-lookup"><span data-stu-id="55e22-121">Rulesets</span></span>
    - <span data-ttu-id="55e22-122">Çözümleyicileri tarafından kullanılan ek dosyalar</span><span class="sxs-lookup"><span data-stu-id="55e22-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="55e22-123">Geçerli kültür (hangi tanılama ve özel durum iletileri üretilen dilin).</span><span class="sxs-lookup"><span data-stu-id="55e22-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="55e22-124">Varsayılan kodlama (veya geçerli kod sayfası) kodlama belirtilmediği takdirde.</span><span class="sxs-lookup"><span data-stu-id="55e22-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="55e22-125">Varlığı, varlığı olmayan ve derleyicinin arama yolları dosyaların içeriğini (örneğin, tarafından belirtilen `/lib` veya `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="55e22-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="55e22-126">CLR platform derleyici çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="55e22-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="55e22-127">Değeri `%LIBPATH%`, Çözümleyicisi bağımlılık yükleniyor etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="55e22-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="55e22-128">Kaynakları genel kullanıma açık olduğunda belirleyici derleme güvenilir bir kaynaktan bir ikili derlenmiş olup olmadığını kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55e22-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="55e22-129">Ayrıca bir sürekli yapı sistemindeki bir ikili değişiklikler bağımlı derleme adımları yürütülebilir gerekip gerekmediğini belirlemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="55e22-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="55e22-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55e22-130">See Also</span></span>  
 [<span data-ttu-id="55e22-131">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="55e22-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="55e22-132">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="55e22-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
