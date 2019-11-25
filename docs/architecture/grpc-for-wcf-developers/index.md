---
title: WCF geliştiricileri için ASP.NET Core gRPC-WCF geliştiricileri için gRPC
description: WCF geliştiricileri için ASP.NET Core 3,0 ' de gRPC hizmetleri oluşturmaya giriş
ms.date: 09/02/2019
ms.openlocfilehash: 3ef513d2397b6f282591dfe6c9b25cd178372a28
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967742"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="5e294-103">WCF Geliştiricileri için ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="5e294-103">ASP.NET Core gRPC for WCF Developers</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="5e294-105">YAYıMLAYAN</span><span class="sxs-lookup"><span data-stu-id="5e294-105">PUBLISHED BY</span></span>

<span data-ttu-id="5e294-106">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="5e294-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="5e294-107">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="5e294-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="5e294-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="5e294-108">One Microsoft Way</span></span>

<span data-ttu-id="5e294-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="5e294-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="5e294-110">Telif hakkı © 2019 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5e294-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="5e294-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="5e294-111">All rights reserved.</span></span> <span data-ttu-id="5e294-112">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e294-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="5e294-113">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="5e294-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="5e294-114">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e294-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="5e294-115">Burada gösterilen bazı örnekler yalnızca gösterim amaçlıdır ve hayal ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="5e294-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="5e294-116">Hiçbir gerçek ilişkilendirme veya bağlantı amaçlanmaz veya çıkarsanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e294-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="5e294-117">Microsoft ve "ticari markalar" Web sayfasındaki https://www.microsoft.com listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="5e294-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="5e294-118">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="5e294-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="5e294-119">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="5e294-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="5e294-120">Geliştirici</span><span class="sxs-lookup"><span data-stu-id="5e294-120">Author:</span></span>

> <span data-ttu-id="5e294-121">Yeniden **işaretle** -BT Teknik Müdürü- [görsel recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="5e294-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="5e294-122">**MDA bu,** teknik yazar</span><span class="sxs-lookup"><span data-stu-id="5e294-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="5e294-123">Edit</span><span class="sxs-lookup"><span data-stu-id="5e294-123">Editors:</span></span>

> <span data-ttu-id="5e294-124">**Maira Wenzel** -SR içerik geliştiricisi-Microsoft</span><span class="sxs-lookup"><span data-stu-id="5e294-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="5e294-125">Giriş</span><span class="sxs-lookup"><span data-stu-id="5e294-125">Introduction</span></span>

<span data-ttu-id="5e294-126">gRPC, ağa bağlı hizmetler ve dağıtılmış uygulamalar oluşturmaya yönelik modern bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="5e294-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="5e294-127">SOAP 'nin platformlar arası birlikte çalışabilirliği ile WCF 'nin NetTCP bağlamalarının performansını düşünün.</span><span class="sxs-lookup"><span data-stu-id="5e294-127">Imagine the performance of WCF's NetTCP bindings with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="5e294-128">, uygulamalar ve hizmetler arasında yüksek performans, düşük bant genişliğine sahip bir iletişim sağlamak için HTTP/2 ve prototip ileti kodlama protokolü üzerinde gRPC derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="5e294-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="5e294-129">.NET, Java, Python, Node. js, go C++ ve daha fazlasını içeren en popüler programlama dilleri ve platformları genelinde sunucu ve istemci kodu üretimini destekler.</span><span class="sxs-lookup"><span data-stu-id="5e294-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, C++ and more.</span></span> <span data-ttu-id="5e294-130">ASP.NET Core 3,0 ' de gRPC için birinci sınıf destek sayesinde, mevcut gRPC araçları ve .NET 4. x kitaplıklarının yanı sıra, kuruluşlarda .NET Core 'u benimsemek isteyen geliştirme ekiplerine yönelik WCF için mükemmel bir alternatif olduğunu düşündük.</span><span class="sxs-lookup"><span data-stu-id="5e294-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, we think it is an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="5e294-131">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="5e294-131">Who should use this guide</span></span>

<span data-ttu-id="5e294-132">Bu kılavuz, daha önce WCF kullanan ve .NET Core 3,0 ve sonraki sürümleri için uygulamalarını modern bir RPC ortamına geçirmeyi arayan .NET Framework veya .NET Core 'da çalışan geliştiriciler için yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5e294-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="5e294-133">Bu kılavuz, yerleşik gRPC araçlarını kullanmak isteyen geliştiriciler için .NET Core 3,0 ' a yükseltmeyi veya kullanmayı düşünürken daha genel kullanım de olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e294-133">The guide may also be of use more generally for developers upgrading or considering upgrading to .NET Core 3.0 who want to use the built-in gRPC tools.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="5e294-134">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="5e294-134">How you can use this guide</span></span>

<span data-ttu-id="5e294-135">Bu, WCF 'ye benzer bir platform olarak belirli bir başvuru ile ASP.NET Core 3,0 ' de gRPC hizmetleri oluşturmaya yönelik kısa bir giriş niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="5e294-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="5e294-136">GRPC 'nin ilkelerini açıklar, her bir kavramı WCF 'nin eşdeğer özellikleriyle birbirleriyle ilgili olarak, mevcut bir WCF uygulamasının gRPC 'ye geçirilmesi için rehberlik sunar.</span><span class="sxs-lookup"><span data-stu-id="5e294-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="5e294-137">Ayrıca, WCF deneyimi olan ve yeni hizmetler oluşturmak üzere gRPC 'yi öğrenmek isteyen geliştiriciler için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5e294-137">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="5e294-138">Örnek uygulamalar, kendi projeleriniz için bir şablon veya başvuru olarak kullanılabilir ve kodu kitap veya örneklerinden kopyalayabilir ve yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e294-138">The sample applications can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="5e294-139">Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="5e294-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="5e294-140">Her bir gövdenin ortak bir terminoloji kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5e294-140">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="5e294-141">Referanslar</span><span class="sxs-lookup"><span data-stu-id="5e294-141">References</span></span>

- <span data-ttu-id="5e294-142">**gRPC Web sitesi**</span><span class="sxs-lookup"><span data-stu-id="5e294-142">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="5e294-143">**Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**</span><span class="sxs-lookup"><span data-stu-id="5e294-143">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="5e294-144">Next</span><span class="sxs-lookup"><span data-stu-id="5e294-144">Next</span></span>](introduction.md)
