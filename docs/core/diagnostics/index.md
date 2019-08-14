---
title: Tanılama araçlarına genel bakış-.NET Core
description: .NET Core uygulamalarını tanılamak için kullanılabilen araçlara ve tekniklere genel bakış.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974128"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="0b795-103">.NET Core 'da hangi tanılama araçları kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="0b795-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="0b795-104">Yazılım her zaman beklediği gibi davranmaz, ancak .NET Core bu sorunları hızlı ve etkili bir şekilde tanılamanıza yardımcı olacak araçlar ve API 'Lere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0b795-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="0b795-105">Bu makale, ihtiyacınız olan çeşitli araçları bulmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="0b795-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggersmanaged-debuggersmd"></a>[<span data-ttu-id="0b795-106">Yönetilen hata ayıklayıcıları</span><span class="sxs-lookup"><span data-stu-id="0b795-106">Managed debuggers</span></span>](managed-debuggers.md)
<span data-ttu-id="0b795-107">Yönetilen hata defterleri, programla etkileşime girebilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="0b795-107">Managed debuggers allow you to interact with your program.</span></span> <span data-ttu-id="0b795-108">Duraklatma, artımlı yürütme, İnceleme ve sürdürme kodunuzun davranışı hakkında fikir verir.</span><span class="sxs-lookup"><span data-stu-id="0b795-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="0b795-109">Hata ayıklayıcı, kolayca yeniden oluşturabileceğiniz işlevsel sorunları tanılamaya yönelik ilk seçenektir.</span><span class="sxs-lookup"><span data-stu-id="0b795-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracinglogging-tracingmd"></a>[<span data-ttu-id="0b795-110">Günlüğe kaydetme ve izleme</span><span class="sxs-lookup"><span data-stu-id="0b795-110">Logging and tracing</span></span>](logging-tracing.md)
<span data-ttu-id="0b795-111">Günlüğe kaydetme ve izleme ilgili teknikler.</span><span class="sxs-lookup"><span data-stu-id="0b795-111">Logging and tracing are related techniques.</span></span> <span data-ttu-id="0b795-112">Günlük dosyaları oluşturmak için kodu işaretleme bölümüne başvururlar.</span><span class="sxs-lookup"><span data-stu-id="0b795-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="0b795-113">Dosyalar, bir programın yaptığı ayrıntıları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0b795-113">The files record the details of what a program does.</span></span> <span data-ttu-id="0b795-114">Bu ayrıntılar, en karmaşık sorunları tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b795-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="0b795-115">Zaman damgalarıyla birleştirildiğinde, bu teknikler performans araştırmaları açısından de değerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b795-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testingtestingindexmd"></a>[<span data-ttu-id="0b795-116">Birim testi</span><span class="sxs-lookup"><span data-stu-id="0b795-116">Unit testing</span></span>](../testing/index.md)
<span data-ttu-id="0b795-117">Birim testi, yüksek kaliteli yazılımların sürekli tümleştirilmesine ve dağıtımına yönelik temel bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="0b795-117">Unit testing is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="0b795-118">Birim testleri, bir şeyi kesen bir erken uyarı sağlayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b795-118">Unit tests are designed to give you an early warning when you break something.</span></span>
