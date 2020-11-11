---
title: Çalışma zamanı kitaplıklarına genel bakış
description: İçindekiler tablosunun çalışma zamanı kitaplıkları bölümüne nelerin ekleneceğini öğrenin.
author: tdykstra
ms.date: 11/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 64bbc13f8c3df3c0c9a02fee4560c9ee3fcc5d62
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507613"
---
# <a name="runtime-libraries-overview"></a><span data-ttu-id="deb3f-103">Çalışma zamanı kitaplıklarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="deb3f-103">Runtime libraries overview</span></span>

<span data-ttu-id="deb3f-104">[Çerçeveye bağımlı uygulamalar](../core/introduction.md#deployment-models)tarafından kullanılmak üzere bir makinede yüklü olan [.NET çalışma zamanına](../core/introduction.md#sdk-and-runtimes), expante standart bir sınıf kitaplıkları kümesi vardır:</span><span class="sxs-lookup"><span data-stu-id="deb3f-104">The [.NET runtime](../core/introduction.md#sdk-and-runtimes), which is installed on a machine for use by [framework-dependent apps](../core/introduction.md#deployment-models), has an expansive standard set of class libraries:</span></span>

* <span data-ttu-id="deb3f-105">Çalışma zamanına dahil olan ve [temel sınıf kitaplıkları (BCL)](glossary.md#bcl)olarak bilinen çekirdek küme.</span><span class="sxs-lookup"><span data-stu-id="deb3f-105">The core set, included in the runtime and known as the [base class libraries (BCL)](glossary.md#bcl).</span></span>
* <span data-ttu-id="deb3f-106">Çalışma zamanına dahil olan ve [çalışma zamanı kitaplıkları](glossary.md#runtime) veya [Framework kitaplıkları](glossary.md#framework)olarak bilinen tüm küme.</span><span class="sxs-lookup"><span data-stu-id="deb3f-106">The complete set, included in the runtime and known as the [runtime libraries](glossary.md#runtime) or [framework libraries](glossary.md#framework).</span></span>
* <span data-ttu-id="deb3f-107">NuGet paketlerinde belirtilen çalışma zamanı kitaplıklarının uzantıları.</span><span class="sxs-lookup"><span data-stu-id="deb3f-107">Extensions to the runtime libraries, provided in NuGet packages.</span></span>

<span data-ttu-id="deb3f-108">Bu kitaplıklar birçok genel ve uygulamaya özel türler, algoritmalar ve yardımcı program işlevselliğine yönelik uygulamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="deb3f-108">These libraries provide implementations for many general and app-specific types, algorithms, and utility functionality.</span></span>

## <a name="base-class-libraries"></a><span data-ttu-id="deb3f-109">Temel sınıf kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="deb3f-109">Base class libraries</span></span>

<span data-ttu-id="deb3f-110">BCL temel türler ve yardımcı işlevler sağlar ve diğer tüm .NET sınıf kitaplıklarının temelini içerir.</span><span class="sxs-lookup"><span data-stu-id="deb3f-110">The BCL provides the foundational types and utility functionality and is the base of all other .NET class libraries.</span></span> <span data-ttu-id="deb3f-111">Bir örnek <xref:System.String?displayProperty=nameWithType> , dizeler ile çalışmaya yönelik API 'ler sağlayan sınıftır.</span><span class="sxs-lookup"><span data-stu-id="deb3f-111">An example is the <xref:System.String?displayProperty=nameWithType> class, which provides APIs for working with strings.</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="deb3f-112">Çalışma zamanı kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="deb3f-112">Runtime libraries</span></span>

<span data-ttu-id="deb3f-113">Çerçeve kitaplıkları olarak da bilinen çalışma zamanı kitaplıkları, ortak görevler için yardımcı API 'Leri sağlamak üzere BCL üzerinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="deb3f-113">Also known as the framework libraries, the runtime libraries build on the BCL to provide utility APIs for common tasks.</span></span> <span data-ttu-id="deb3f-114">[Serileştirme kitaplıkları](serialization/index.md)bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="deb3f-114">An example is the [serialization libraries](serialization/index.md).</span></span>

## <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="deb3f-115">Çalışma zamanı kitaplıklarının uzantıları</span><span class="sxs-lookup"><span data-stu-id="deb3f-115">Extensions to the runtime libraries</span></span>

<span data-ttu-id="deb3f-116">Çalışma zamanı kitaplıklarının bazıları, çerçeveye bağımlı uygulamalar için yüklenen çalışma zamanına yerleşik olmak yerine NuGet paketlerinde sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="deb3f-116">Some of the runtime libraries are provided in NuGet packages rather than built-in to the runtime that is installed for framework-dependent apps.</span></span> <span data-ttu-id="deb3f-117">[.Net günlüğü API 'sine](../core/extensions/logging.md)örnek bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="deb3f-117">An example is the [.NET Logging API](../core/extensions/logging.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="deb3f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deb3f-118">See also</span></span>

* [<span data-ttu-id="deb3f-119">.NET’e giriş</span><span class="sxs-lookup"><span data-stu-id="deb3f-119">Introduction to .NET</span></span>](../core/introduction.md)
* [<span data-ttu-id="deb3f-120">.NET SDK veya çalışma zamanı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="deb3f-120">Install .NET SDK or runtime</span></span>](../core/install/index.yml)
* [<span data-ttu-id="deb3f-121">Kullanılacak yüklü .NET SDK 'sını veya çalışma zamanı sürümünü seçin</span><span class="sxs-lookup"><span data-stu-id="deb3f-121">Select the installed .NET SDK or runtime version to use</span></span>](../core/versions/selection.md)
* [<span data-ttu-id="deb3f-122">Çerçeveye bağımlı uygulamalar yayımlama</span><span class="sxs-lookup"><span data-stu-id="deb3f-122">Publish framework-dependent apps</span></span>](../core/deploying/index.md#publish-framework-dependent)
