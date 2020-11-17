---
title: Çalışma zamanı kitaplıklarına genel bakış
description: İçindekiler tablosunun çalışma zamanı kitaplıkları bölümüne nelerin ekleneceğini öğrenin.
author: tdykstra
ms.date: 11/12/2020
ms.openlocfilehash: 5a8f888e1778553e2968277738cfef5134f11589
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687896"
---
# <a name="runtime-libraries-overview"></a><span data-ttu-id="fa2ab-103">Çalışma zamanı kitaplıklarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="fa2ab-103">Runtime libraries overview</span></span>

<span data-ttu-id="fa2ab-104">[Framework 'e bağımlı uygulamalar](../core/introduction.md#deployment-models)tarafından kullanılmak üzere bir makineye yüklenen [.NET çalışma zamanı](../core/introduction.md#sdk-and-runtimes), [çalışma zamanı kitaplıkları](glossary.md#runtime), [çerçeve kitaplıkları](glossary.md#framework-libraries)veya [temel sınıf kitaplığı (BCL)](glossary.md#bcl)olarak bilinen, expante standart bir sınıf kitaplıkları kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fa2ab-104">The [.NET runtime](../core/introduction.md#sdk-and-runtimes), which is installed on a machine for use by [framework-dependent apps](../core/introduction.md#deployment-models), has an expansive standard set of class libraries, known as [runtime libraries](glossary.md#runtime), [framework libraries](glossary.md#framework-libraries), or the [base class library (BCL)](glossary.md#bcl).</span></span> <span data-ttu-id="fa2ab-105">Ayrıca, NuGet paketlerinde belirtilen çalışma zamanı kitaplıklarının uzantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="fa2ab-105">In addition, there are extensions to the runtime libraries, provided in NuGet packages.</span></span>

<span data-ttu-id="fa2ab-106">Bu kitaplıklar birçok genel ve uygulamaya özel türler, algoritmalar ve yardımcı program işlevselliğine yönelik uygulamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa2ab-106">These libraries provide implementations for many general and app-specific types, algorithms, and utility functionality.</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="fa2ab-107">Çalışma zamanı kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="fa2ab-107">Runtime libraries</span></span>

<span data-ttu-id="fa2ab-108">Bu kitaplıklar temel türler ve yardımcı işlevler sağlar ve diğer tüm .NET sınıf kitaplıklarının tabtemeldir.</span><span class="sxs-lookup"><span data-stu-id="fa2ab-108">These libraries provide the foundational types and utility functionality and are the base of all other .NET class libraries.</span></span> <span data-ttu-id="fa2ab-109">Bir örnek <xref:System.String?displayProperty=nameWithType> , dizeler ile çalışmaya yönelik API 'ler sağlayan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="fa2ab-109">An example is the <xref:System.String?displayProperty=nameWithType> class, which provides APIs for working with strings.</span></span> <span data-ttu-id="fa2ab-110">[Serileştirme kitaplıkları](serialization/index.md)başka bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="fa2ab-110">Another example is the [serialization libraries](serialization/index.md).</span></span>

## <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="fa2ab-111">Çalışma zamanı kitaplıklarının uzantıları</span><span class="sxs-lookup"><span data-stu-id="fa2ab-111">Extensions to the runtime libraries</span></span>

<span data-ttu-id="fa2ab-112">Bazı kitaplıklar, çalışma zamanının [paylaşılan çerçevesine](glossary.md#shared-framework)dahil olmak yerine NuGet paketlerinde sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa2ab-112">Some libraries are provided in NuGet packages rather than included in the runtime's [shared framework](glossary.md#shared-framework).</span></span> <span data-ttu-id="fa2ab-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="fa2ab-113">For example:</span></span>

* [<span data-ttu-id="fa2ab-114">Günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="fa2ab-114">Logging</span></span>](../core/extensions/logging.md)
* [<span data-ttu-id="fa2ab-115">Bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="fa2ab-115">Dependency injection</span></span>](../core/extensions/dependency-injection.md)
* [<span data-ttu-id="fa2ab-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa2ab-116">Configuration</span></span>](../core/extensions/configuration.md)

## <a name="see-also"></a><span data-ttu-id="fa2ab-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa2ab-117">See also</span></span>

* [<span data-ttu-id="fa2ab-118">.NET’e giriş</span><span class="sxs-lookup"><span data-stu-id="fa2ab-118">Introduction to .NET</span></span>](../core/introduction.md)
* [<span data-ttu-id="fa2ab-119">.NET SDK veya çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="fa2ab-119">Install .NET SDK or runtime</span></span>](../core/install/index.yml)
* [<span data-ttu-id="fa2ab-120">Kullanılacak yüklü .NET SDK 'sını veya çalışma zamanı sürümünü seçin</span><span class="sxs-lookup"><span data-stu-id="fa2ab-120">Select the installed .NET SDK or runtime version to use</span></span>](../core/versions/selection.md)
* [<span data-ttu-id="fa2ab-121">Çerçeveye bağımlı uygulamalar yayımlama</span><span class="sxs-lookup"><span data-stu-id="fa2ab-121">Publish framework-dependent apps</span></span>](../core/deploying/index.md#publish-framework-dependent)
