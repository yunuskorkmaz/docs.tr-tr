---
title: .NET uygulamalarını genelleştirmek ve yerelleştirme
description: Dünya çapında hazırlanma uygulaması geliştirmeyi öğrenin. .NET ' te Genelleştirme, Yerelleştirilebilirlik incelemesi ve yerelleştirme hakkında bilgi edinin.
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: a3894b7bf9b8aa013b346c169d21c6db270fe987
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600795"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="98be2-104">.NET uygulamalarını genelleştirmek ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="98be2-104">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="98be2-105">Bir veya daha fazla dilde yerelleştirilebilecek bir uygulama da dahil olmak üzere dünya çapında kullanılabilir bir uygulama geliştirme, üç adımdan oluşur: Genelleştirme, Yerelleştirilebilirlik incelemesi ve yerelleştirme.</span><span class="sxs-lookup"><span data-stu-id="98be2-105">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="98be2-106">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="98be2-106">Globalization</span></span>](globalization.md)

<span data-ttu-id="98be2-107">Bu adım kültür ve dil açısından nötr olan ve tüm kullanıcılar için yerelleştirilmiş kullanıcı arabirimleri ve bölgesel verileri destekleyen bir uygulamanın tasarlanması ve kodlanmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="98be2-107">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="98be2-108">Tasarım yapma ve kültüre özgü varsayımlara dayalı olmayan kararları programlama ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="98be2-108">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="98be2-109">Global uygulamalar yerelleştirilmez, ancak daha sonra bir veya birden çok dile görece kolay yerelleştirilebilecek şekilde tasarlanır ve yazılırlar.</span><span class="sxs-lookup"><span data-stu-id="98be2-109">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="98be2-110">Yerelleştirilebilirlik incelemesi</span><span class="sxs-lookup"><span data-stu-id="98be2-110">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="98be2-111">Bu adım, bir uygulamanın kod ve tasarımının, kolayca yerelleştirilebilir olmasını sağlamak ve yerelleştirme için olası engelleri tanımlamak üzere gözden geçirilmesi ve uygulamanın yürütülebilir kodunun kaynaklarından ayrı olduğunun doğrulanması ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="98be2-111">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="98be2-112">Genelleştirme aşaması etkili olduysa, yerelleştirme incelemesi, genelleştirme sırasında yapılan tasarım ve kodlama seçimlerini onaylar.</span><span class="sxs-lookup"><span data-stu-id="98be2-112">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="98be2-113">Yerelleştirilebilirlik aşaması, bir uygulamanın kaynak kodunu yerelleştirme aşamasında değiştirmek zorunda kalmamanızı sağlayacak şekilde geri kalan sorunları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="98be2-113">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="98be2-114">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="98be2-114">Localization</span></span>](localization.md)

<span data-ttu-id="98be2-115">Bu adım özel kültürler veya bölgeler için bir uygulamanın özelleştirilmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="98be2-115">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="98be2-116">Genelleştirme ve yerelleştirme adımları doğru olarak gerçekleştirilmişse, yerelleştirme, öncelikli olarak kullanıcı arabirimini çevirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="98be2-116">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="98be2-117">Aşağıdaki üç adımı izlemenin iki avantajı vardır:</span><span class="sxs-lookup"><span data-stu-id="98be2-117">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="98be2-118">ABD İngilizcesi gibi tek bir kültürü desteklemek için tasarlanmış bir uygulamayı ek kültürleri desteklemek üzere yükseltmek zorunda kalmanızı önler.</span><span class="sxs-lookup"><span data-stu-id="98be2-118">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="98be2-119">Daha kararlı ve daha az hatası olan yerelleştirilmiş uygulamalar olarak sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="98be2-119">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="98be2-120">.NET, dünya çapında ve yerelleştirilmiş uygulamaların geliştirilmesi için kapsamlı destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="98be2-120">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="98be2-121">Özellikle, .NET sınıf kitaplığındaki birçok üye türü, geçerli kullanıcının kültürünün veya belirtilen kültürün kurallarını yansıtan değerler döndürerek Genelleştirme 'ye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="98be2-121">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="98be2-122">Ayrıca, .NET, bir uygulamayı yerelleştirme işlemini kolaylaştıran uydu derlemelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="98be2-122">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="98be2-123">Daha fazla bilgi için bkz. [Genelleştirme belgeleri](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="98be2-123">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="98be2-124">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="98be2-124">In this section</span></span>

[<span data-ttu-id="98be2-125">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="98be2-125">Globalization</span></span>](globalization.md)

<span data-ttu-id="98be2-126">Nötr kültüre ve nötr dile sahip bir uygulama tasarlamayı ve kodlamayı da içeren, dünya çapında kullanılmaya hazır uygulama bir oluşturmanın ilk aşamasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="98be2-126">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="98be2-127">.NET Genelleştirme ve ıCU</span><span class="sxs-lookup"><span data-stu-id="98be2-127">.NET globalization and ICU</span></span>](globalization-icu.md)

<span data-ttu-id="98be2-128">.NET Genelleştirme 'nin [Unicode (ıCU) Için Uluslararası bileşenleri](http://site.icu-project.org/home)nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="98be2-128">Describes how .NET globalization uses [International Components for Unicode (ICU)](http://site.icu-project.org/home).</span></span>

[<span data-ttu-id="98be2-129">Yerelleştirilebilirlik incelemesi</span><span class="sxs-lookup"><span data-stu-id="98be2-129">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="98be2-130">Yerelleştirmede potansiyel bariyerler tanımlamayı da içeren yerelleştirilmiş uygulama oluşturmanın ikinci aşamasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="98be2-130">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="98be2-131">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="98be2-131">Localization</span></span>](localization.md)

<span data-ttu-id="98be2-132">Özel bölgeler ve kültürler için bir uygulamanın kullanıcı arabirimini özelleştirmeyi içeren yerelleştirilmiş bir uygulama oluşturmanın son adımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="98be2-132">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="98be2-133">Kültüre duyarsız dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="98be2-133">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="98be2-134">Kültüre duyarsız sonuçlar elde etmek için varsayılan olarak kültüre duyarlı olan .NET yöntemlerinin ve sınıflarının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="98be2-134">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="98be2-135">Dünya çapında kullanmaya yönelik uygulamalar geliştirmek için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="98be2-135">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="98be2-136">Genelleştirme, yerelleştirme ve dünya çapında kullanılmaya hazır ASP.NET uygulamaları geliştirmek için izlenebilecek en iyi uygulamaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="98be2-136">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="98be2-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="98be2-137">Reference</span></span>

- <span data-ttu-id="98be2-138"><xref:System.Globalization?displayProperty=nameWithType>uzayına</span><span class="sxs-lookup"><span data-stu-id="98be2-138"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="98be2-139">Bu ad alanındaki, dil, ülke/bölge, kullanılan takvimler, tarihler için biçim desenleri, para birimi, sayılar ve dizeler için sıralama düzeni gibi kültürle ilişkili bilgileri tanımlayan sınıflar içerir</span><span class="sxs-lookup"><span data-stu-id="98be2-139">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="98be2-140"><xref:System.Resources>uzayına</span><span class="sxs-lookup"><span data-stu-id="98be2-140"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="98be2-141">Kaynaklar oluşturmak, düzenlemek ve kullanmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="98be2-141">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="98be2-142"><xref:System.Text>uzayına</span><span class="sxs-lookup"><span data-stu-id="98be2-142"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="98be2-143">ASCII, ANSI, Unicode ve diğer karakter kodlamalarını temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="98be2-143">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="98be2-144">Resgen. exe (kaynak dosya Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="98be2-144">Resgen.exe (Resource File Generator)</span></span>](../../framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="98be2-145">.txt dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını ortak dil çalışma zamanı ikili .resources dosyalarına dönüştürmek için Resgen.exe öğesinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="98be2-145">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="98be2-146">Winres. exe (Windows Forms Kaynak Düzenleyicisi)</span><span class="sxs-lookup"><span data-stu-id="98be2-146">Winres.exe (Windows Forms Resource Editor)</span></span>](../../framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="98be2-147">Windows Forms formlarını yerelleştirmek için Winres.exe yürütme dosyasının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="98be2-147">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
