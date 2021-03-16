---
description: Çeşitli C# derleyici seçenekleri. Bu seçenekler derleyiciye genel seçenekler sağlar.
title: Diğer kategorilere sığmayan C# derleyici seçenekleri
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- ResponseFiles compiler option [C#]
- NoLogo compiler option [C#]
- NoConfig compiler option [C#]
ms.openlocfilehash: ec7d9c3685c9acb5ca3cda28aca55abb26b836cf
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482914"
---
# <a name="miscellaneous-c-compiler-options"></a><span data-ttu-id="4b503-104">Çeşitli C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4b503-104">Miscellaneous C# Compiler Options</span></span>

<span data-ttu-id="4b503-105">Aşağıdaki seçenekler çeşitli derleyici davranışlarını denetler.</span><span class="sxs-lookup"><span data-stu-id="4b503-105">The following options control miscellaneous compiler behavior.</span></span> <span data-ttu-id="4b503-106">Yeni MSBuild sözdizimi **kalın** olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4b503-106">The new MSBuild syntax is shown in **Bold**.</span></span> <span data-ttu-id="4b503-107">Eski *csc.exe* sözdizimi içinde gösterilir `code style` .</span><span class="sxs-lookup"><span data-stu-id="4b503-107">The older *csc.exe* syntax is shown in `code style`.</span></span>

- <span data-ttu-id="4b503-108">**ResponseFiles**  /  `-@` : daha fazla seçenek için yanıt dosyasını okuyun.</span><span class="sxs-lookup"><span data-stu-id="4b503-108">**ResponseFiles** / `-@`: Read response file for more options.</span></span>
- <span data-ttu-id="4b503-109">  /  Nologo `-nologo` : Derleyici telif hakkı iletisini bastır.</span><span class="sxs-lookup"><span data-stu-id="4b503-109">**NoLogo** / `-nologo` : Suppress compiler copyright message.</span></span>
- <span data-ttu-id="4b503-110">**Noconfig**  /  `-noconfig` : *CSC. rsp* dosyasını otomatik olarak eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="4b503-110">**NoConfig** / `-noconfig`: Don't auto include *CSC.RSP* file.</span></span>

## <a name="responsefiles"></a><span data-ttu-id="4b503-111">Yanıt dosyaları</span><span class="sxs-lookup"><span data-stu-id="4b503-111">ResponseFiles</span></span>

<span data-ttu-id="4b503-112">**ResponseFiles** seçeneği, derlemek için derleyici seçeneklerini ve kaynak kodu dosyalarını içeren bir dosya belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4b503-112">The **ResponseFiles** option lets you specify a file that contains compiler options and source code files to compile.</span></span>

```xml
<ResponseFiles>response_file</ResponseFiles>
```

<span data-ttu-id="4b503-113">, `response_file` Derlemek için derleyici seçeneklerini veya kaynak kodu dosyalarını listeleyen dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b503-113">The `response_file` specifies the file that lists compiler options or source code files to compile.</span></span> <span data-ttu-id="4b503-114">Derleyici seçenekleri ve kaynak kodu dosyaları, derleyici tarafından komut satırında belirtildikleri gibi işlenecek.</span><span class="sxs-lookup"><span data-stu-id="4b503-114">The compiler options and source code files will be processed by the compiler as if they had been specified on the command line.</span></span> <span data-ttu-id="4b503-115">Bir derlemede birden fazla yanıt dosyası belirtmek için, birden çok yanıt dosyası seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="4b503-115">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="4b503-116">Bir yanıt dosyasında, bir satırda birden çok derleyici seçeneği ve kaynak kodu dosyası görünebilir.</span><span class="sxs-lookup"><span data-stu-id="4b503-116">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="4b503-117">Tek bir derleyici seçenek belirtiminin tek bir satırda görünmesi gerekir (birden çok satıra yayılamaz).</span><span class="sxs-lookup"><span data-stu-id="4b503-117">A single compiler option specification must appear on one line (can't span multiple lines).</span></span> <span data-ttu-id="4b503-118">Yanıt dosyaları # simgesiyle başlayan açıklamalara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b503-118">Response files can have comments that begin with the # symbol.</span></span> <span data-ttu-id="4b503-119">Bir yanıt dosyası içinden derleyici seçeneklerinin belirtilmesi, komut satırında bu komutları verme gibidir.</span><span class="sxs-lookup"><span data-stu-id="4b503-119">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="4b503-120">Derleyici, okunan komut seçeneklerini işler.</span><span class="sxs-lookup"><span data-stu-id="4b503-120">The compiler processes the command options as they're read.</span></span> <span data-ttu-id="4b503-121">Komut satırı bağımsız değişkenleri, yanıt dosyalarında daha önce listelenen seçenekleri geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b503-121">Command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="4b503-122">Buna karşılık, bir yanıt dosyasındaki seçenekler, önceden komut satırında veya diğer yanıt dosyalarında listelenen seçenekleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4b503-122">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span> <span data-ttu-id="4b503-123">C#, csc.exe dosyası ile aynı dizinde bulunan CSC. rsp dosyasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b503-123">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="4b503-124">Yanıt dosyası biçimi hakkında daha fazla bilgi için bkz. [**noconfig**](#noconfig).</span><span class="sxs-lookup"><span data-stu-id="4b503-124">For more information about the response file format, see [**NoConfig**](#noconfig).</span></span> <span data-ttu-id="4b503-125">Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4b503-125">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span> <span data-ttu-id="4b503-126">Örnek yanıt dosyasından birkaç satır aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4b503-126">The following are a few lines from a sample response file:</span></span>

```console
# build the first output file
-target:exe -out:MyExe.exe source1.cs source2.cs
```

## <a name="nologo"></a><span data-ttu-id="4b503-127">NoLogo</span><span class="sxs-lookup"><span data-stu-id="4b503-127">NoLogo</span></span>

<span data-ttu-id="4b503-128">**Nologo** seçeneği, derleyici başlatıldığında ve derleme sırasında bilgilendirici iletileri görüntülerken oturum açma başlığının görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="4b503-128">The **NoLogo** option suppresses display of the sign-on banner when the compiler starts up and display of informational messages during compiling.</span></span>

```xml
<NoLogo>true</NoLogo>
```

## <a name="noconfig"></a><span data-ttu-id="4b503-129">NoConfig</span><span class="sxs-lookup"><span data-stu-id="4b503-129">NoConfig</span></span>

<span data-ttu-id="4b503-130">**Noconfig** seçeneği derleyicinin *CSC. rsp* dosyasıyla derlenmeyeceğini söyler.</span><span class="sxs-lookup"><span data-stu-id="4b503-130">The **NoConfig** option tells the compiler not to compile with the *csc.rsp* file.</span></span>

```xml
<NoConfig>true</NoConfig>
```

<span data-ttu-id="4b503-131">*CSC. rsp* dosyası .NET Framework ile gönderilen tüm derlemelere başvurur.</span><span class="sxs-lookup"><span data-stu-id="4b503-131">The *csc.rsp* file references all the assemblies shipped with .NET Framework.</span></span> <span data-ttu-id="4b503-132">Visual Studio .NET geliştirme ortamının içerdiği gerçek başvurular proje türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4b503-132">The actual references that the Visual Studio .NET development environment includes depend on the project type.</span></span> <span data-ttu-id="4b503-133">*CSC. rsp* dosyasını değiştirebilir ve her derlemede dahil edilecek ek derleyici seçeneklerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b503-133">You can modify the *csc.rsp* file and specify additional compiler options that should be included in every compilation.</span></span> <span data-ttu-id="4b503-134">Derleyicinin *CSC. rsp* dosyasındaki ayarları araması ve kullanması Istemiyorsanız, **noconfig**' i belirtin.</span><span class="sxs-lookup"><span data-stu-id="4b503-134">If you don't want the compiler to look for and use the settings in the *csc.rsp* file, specify **NoConfig**.</span></span> <span data-ttu-id="4b503-135">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4b503-135">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>
