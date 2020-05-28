---
title: WCF geliştiricileri için ASP.NET Core gRPC-WCF geliştiricileri için gRPC
description: WCF geliştiricileri için ASP.NET Core 3,0 ' de gRPC hizmetleri oluşturmaya giriş
ms.date: 09/02/2019
ms.openlocfilehash: 6e18ecfdb8fcbe20f71fd0a7c77076166451427a
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144363"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="d5c19-103">WCF Geliştiricileri için ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="d5c19-103">ASP.NET Core gRPC for WCF Developers</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="d5c19-105">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="d5c19-105">PUBLISHED BY</span></span>

<span data-ttu-id="d5c19-106">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="d5c19-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="d5c19-107">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="d5c19-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="d5c19-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="d5c19-108">One Microsoft Way</span></span>

<span data-ttu-id="d5c19-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="d5c19-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="d5c19-110">Telif hakkı © 2019 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d5c19-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="d5c19-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="d5c19-111">All rights reserved.</span></span> <span data-ttu-id="d5c19-112">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="d5c19-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="d5c19-113">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="d5c19-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="d5c19-114">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d5c19-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="d5c19-115">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="d5c19-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="d5c19-116">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5c19-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="d5c19-117">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="d5c19-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="d5c19-118">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="d5c19-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="d5c19-119">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="d5c19-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="d5c19-120">Düzenliyor</span><span class="sxs-lookup"><span data-stu-id="d5c19-120">Authors:</span></span>

> <span data-ttu-id="d5c19-121">Yeniden **işaretle** -BT Teknik Müdürü- [görsel recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="d5c19-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="d5c19-122">**MDA bu,** teknik yazar</span><span class="sxs-lookup"><span data-stu-id="d5c19-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="d5c19-123">Düzenleyen</span><span class="sxs-lookup"><span data-stu-id="d5c19-123">Editor:</span></span>

> <span data-ttu-id="d5c19-124">**Maira Wenzel** -SR. Content Developer-Microsoft</span><span class="sxs-lookup"><span data-stu-id="d5c19-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="d5c19-125">Giriş</span><span class="sxs-lookup"><span data-stu-id="d5c19-125">Introduction</span></span>

<span data-ttu-id="d5c19-126">gRPC, ağa bağlı hizmetler ve dağıtılmış uygulamalar oluşturmaya yönelik modern bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="d5c19-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="d5c19-127">SOAP 'ın platformlar arası birlikte çalışabilirliğiyle birlikte Windows Communication Foundation (WCF) NetTCP bağlamalarının performansını düşünün.</span><span class="sxs-lookup"><span data-stu-id="d5c19-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="d5c19-128">, uygulamalar ve hizmetler arasında yüksek performans, düşük bant genişliğine sahip bir iletişim sağlamak için HTTP/2 ve prototip ileti kodlama protokolü üzerinde gRPC derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="d5c19-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="d5c19-129">.NET, Java, Python, Node. js, Go ve C++ dahil çoğu popüler programlama dili ve platformu genelinde sunucu ve istemci kodu oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="d5c19-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="d5c19-130">ASP.NET Core 3,0 ' de gRPC için birinci sınıf destek sayesinde, mevcut gRPC araçları ve .NET 4. x kitaplıklarının yanı sıra, kuruluşlarda .NET Core 'u benimsemek isteyen geliştirme ekiplerine yönelik WCF için mükemmel bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="d5c19-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="d5c19-131">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="d5c19-131">Who should use this guide</span></span>

<span data-ttu-id="d5c19-132">Bu kılavuz, daha önce WCF kullanan .NET Framework veya .NET Core 'da çalışan geliştiriciler için yazılmıştır ve uygulamalarını .NET Core 3,0 ve üzeri sürümler için modern bir RPC ortamına geçirmeyi arayan kişiler.</span><span class="sxs-lookup"><span data-stu-id="d5c19-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="d5c19-133">Daha genel olarak, yükseltme yapıyorsanız veya yükseltmeyi .NET Core 3,0 ' e ve yerleşik gRPC araçlarını kullanmak istiyorsanız, bu kılavuz de yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="d5c19-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="d5c19-134">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="d5c19-134">How you can use this guide</span></span>

<span data-ttu-id="d5c19-135">Bu, ASP.NET Core 3,0 ' de gRPC hizmetlerini, benzer bir platform olarak WCF 'ye belirli bir şekilde oluşturmaya yönelik kısa bir giriş niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="d5c19-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="d5c19-136">GRPC 'nin ilkelerini açıklar, her bir kavramı WCF 'nin eşdeğer özellikleriyle birbirleriyle ilgili olarak, mevcut bir WCF uygulamasının gRPC 'ye geçirilmesi için rehberlik sunar.</span><span class="sxs-lookup"><span data-stu-id="d5c19-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="d5c19-137">Ayrıca, WCF ile karşılaşan ve yeni hizmetler oluşturmak üzere gRPC 'yi öğrenmek isteyen geliştiriciler için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5c19-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="d5c19-138">Örnek uygulamaları kendi projeleriniz için bir şablon veya başvuru olarak kullanabilir ve kodu kitap veya örneklerinden kopyalayabilir ve yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5c19-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="d5c19-139">Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="d5c19-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="d5c19-140">Her birinin ortak bir terim kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d5c19-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="d5c19-141">Başvurular</span><span class="sxs-lookup"><span data-stu-id="d5c19-141">References</span></span>

- <span data-ttu-id="d5c19-142">**gRPC Web sitesi**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="d5c19-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="d5c19-143">**Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapma**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="d5c19-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d5c19-144">Sonraki</span><span class="sxs-lookup"><span data-stu-id="d5c19-144">Next</span></span>](introduction.md)
