---
title: WCF geliştiricileri için ASP.NET Core gRPC-WCF geliştiricileri için gRPC
description: WCF geliştiricileri için ASP.NET Core 5,0 ' de gRPC hizmetleri oluşturmaya giriş
ms.date: 01/06/2021
ms.openlocfilehash: 26cce6bb784c08a5b59623ff5882fcf2fbb9e9ac
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970199"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="bdb11-103">WCF Geliştiricileri için ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="bdb11-103">ASP.NET Core gRPC for WCF Developers</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="bdb11-105">SÜRÜM v 1.0.1-ASP.NET Core 5,0 ' ye güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="bdb11-105">EDITION v1.0.1 - Updated to ASP.NET Core 5.0</span></span>

<span data-ttu-id="bdb11-106">Kitap güncelleştirmeleri ve topluluk katkılarına yönelik [changelog](https://aka.ms/grpc-ebook-changelog) 'u inceleyin.</span><span class="sxs-lookup"><span data-stu-id="bdb11-106">Refer [changelog](https://aka.ms/grpc-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="bdb11-107">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="bdb11-107">PUBLISHED BY</span></span>

<span data-ttu-id="bdb11-108">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="bdb11-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="bdb11-109">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="bdb11-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="bdb11-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="bdb11-110">One Microsoft Way</span></span>

<span data-ttu-id="bdb11-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="bdb11-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="bdb11-112">Telif hakkı © 2021 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bdb11-112">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="bdb11-113">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="bdb11-113">All rights reserved.</span></span> <span data-ttu-id="bdb11-114">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="bdb11-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="bdb11-115">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="bdb11-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="bdb11-116">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bdb11-116">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="bdb11-117">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="bdb11-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="bdb11-118">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bdb11-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="bdb11-119">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="bdb11-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="bdb11-120">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="bdb11-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="bdb11-121">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="bdb11-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="bdb11-122">Düzenliyor</span><span class="sxs-lookup"><span data-stu-id="bdb11-122">Authors:</span></span>

> <span data-ttu-id="bdb11-123">Yeniden **işaretle** -BT Teknik Müdürü- [görsel recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="bdb11-123">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="bdb11-124">**MDA bu,** teknik yazar</span><span class="sxs-lookup"><span data-stu-id="bdb11-124">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="bdb11-125">Düzenleyen</span><span class="sxs-lookup"><span data-stu-id="bdb11-125">Editor:</span></span>

> <span data-ttu-id="bdb11-126">**Maira Wenzel** -SR. Content Developer-Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdb11-126">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="bdb11-127">Giriş</span><span class="sxs-lookup"><span data-stu-id="bdb11-127">Introduction</span></span>

<span data-ttu-id="bdb11-128">gRPC, ağa bağlı hizmetler ve dağıtılmış uygulamalar oluşturmaya yönelik modern bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="bdb11-128">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="bdb11-129">SOAP 'ın platformlar arası birlikte çalışabilirliğiyle birlikte Windows Communication Foundation (WCF) NetTCP bağlamalarının performansını düşünün.</span><span class="sxs-lookup"><span data-stu-id="bdb11-129">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="bdb11-130">, uygulamalar ve hizmetler arasında yüksek performans, düşük bant genişliğine sahip bir iletişim sağlamak için HTTP/2 ve prototip ileti kodlama protokolü üzerinde gRPC derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="bdb11-130">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="bdb11-131">.NET, Java, Python, Node.js, Go ve C++ gibi popüler programlama dilleri ve platformları genelinde sunucu ve istemci kodu üretimini destekler.</span><span class="sxs-lookup"><span data-stu-id="bdb11-131">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="bdb11-132">ASP.NET Core 5,0 ' de gRPC için birinci sınıf destek sayesinde, .NET Framework 4. x için mevcut gRPC araçları ve kitaplıklarının yanı sıra, kuruluşlarda .NET benimsemek isteyen geliştirme ekiplerine yönelik WCF için çok iyi bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="bdb11-132">With the first-class support for gRPC in ASP.NET Core 5.0, alongside the existing gRPC tools and libraries for .NET Framework 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="bdb11-133">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="bdb11-133">Who should use this guide</span></span>

<span data-ttu-id="bdb11-134">Bu kılavuz, daha önce WCF kullanan .NET Framework veya .NET üzerinde çalışan geliştiriciler için yazılmıştır ve uygulamalarını .NET Core 3,0 ve sonraki sürümleri için modern bir RPC ortamına geçirmeye yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bdb11-134">This guide was written for developers working in .NET Framework or .NET who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="bdb11-135">Daha genel olarak, yükseltme yapıyorsanız, .NET 5 ' e yükseltme yapıyorsanız ve yerleşik gRPC araçlarını kullanmak istiyorsanız, bu kılavuz de yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="bdb11-135">More generally, if you are upgrading, or considering upgrading, to .NET 5, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="bdb11-136">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="bdb11-136">How you can use this guide</span></span>

<span data-ttu-id="bdb11-137">Bu, ASP.NET Core 5,0 ' de gRPC hizmetlerini, benzer bir platform olarak WCF 'ye belirli bir şekilde oluşturmaya yönelik kısa bir giriş niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="bdb11-137">This is a short introduction to building gRPC Services in ASP.NET Core 5.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="bdb11-138">GRPC 'nin ilkelerini açıklar, her bir kavramı WCF 'nin eşdeğer özellikleriyle birbirleriyle ilgili olarak, mevcut bir WCF uygulamasının gRPC 'ye geçirilmesi için rehberlik sunar.</span><span class="sxs-lookup"><span data-stu-id="bdb11-138">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="bdb11-139">Ayrıca, WCF ile karşılaşan ve yeni hizmetler oluşturmak üzere gRPC 'yi öğrenmek isteyen geliştiriciler için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bdb11-139">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="bdb11-140">Örnek uygulamaları kendi projeleriniz için bir şablon veya başvuru olarak kullanabilir ve kodu kitap veya örneklerinden kopyalayabilir ve yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdb11-140">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="bdb11-141">Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="bdb11-141">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="bdb11-142">Her birinin ortak bir terim kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="bdb11-142">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="bdb11-143">Başvurular</span><span class="sxs-lookup"><span data-stu-id="bdb11-143">References</span></span>

- <span data-ttu-id="bdb11-144">**gRPC Web sitesi**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="bdb11-144">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="bdb11-145">**Sunucu uygulamaları için .NET 5 ve .NET Framework arasında seçim yapma**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="bdb11-145">**Choosing between .NET 5 and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="bdb11-146">Sonraki</span><span class="sxs-lookup"><span data-stu-id="bdb11-146">Next</span></span>](introduction.md)
