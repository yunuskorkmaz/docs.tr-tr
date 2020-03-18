---
title: WCF Geliştiricileri için ASP.NET Core gRPC - WCF Geliştiricileri için gRPC
description: WCF geliştiricileri için Core 3.0'ASP.NET gRPC hizmetleri oluşturmaya giriş
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543241"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="45fba-103">WCF Geliştiricileri için ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="45fba-103">ASP.NET Core gRPC for WCF Developers</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="45fba-105">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="45fba-105">PUBLISHED BY</span></span>

<span data-ttu-id="45fba-106">Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="45fba-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="45fba-107">Microsoft Corporation'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="45fba-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="45fba-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="45fba-108">One Microsoft Way</span></span>

<span data-ttu-id="45fba-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="45fba-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="45fba-110">Telif Hakkı © 2019 Microsoft Corporation tarafından</span><span class="sxs-lookup"><span data-stu-id="45fba-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="45fba-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="45fba-111">All rights reserved.</span></span> <span data-ttu-id="45fba-112">Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="45fba-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="45fba-113">Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="45fba-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="45fba-114">URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.</span><span class="sxs-lookup"><span data-stu-id="45fba-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="45fba-115">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="45fba-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="45fba-116">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="45fba-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="45fba-117">Microsoft ve "Ticari https://www.microsoft.com Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="45fba-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="45fba-118">Docker balina logosu, Docker, Inc. şirketinin izni yle kullanılan tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="45fba-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="45fba-119">Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="45fba-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="45fba-120">Yazar:</span><span class="sxs-lookup"><span data-stu-id="45fba-120">Authors:</span></span>

> <span data-ttu-id="45fba-121">**Mark Rendle** - Baş Teknik Sorumlu - [Görsel Recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="45fba-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="45fba-122">**Miranda Steiner** - Teknik Yazar</span><span class="sxs-lookup"><span data-stu-id="45fba-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="45fba-123">Düzenleyicisi:</span><span class="sxs-lookup"><span data-stu-id="45fba-123">Editor:</span></span>

> <span data-ttu-id="45fba-124">**Maira Wenzel** - Sr. İçerik Geliştiricisi - Microsoft</span><span class="sxs-lookup"><span data-stu-id="45fba-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="45fba-125">Giriş</span><span class="sxs-lookup"><span data-stu-id="45fba-125">Introduction</span></span>

<span data-ttu-id="45fba-126">gRPC, ağa bağlı hizmetler ve dağıtılmış uygulamalar oluşturmak için modern bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="45fba-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="45fba-127">Windows Communication Foundation (WCF) NetTCP bağlamalarının performansını, SOAP'ın çapraz platform birlikte çalışabilirliğiyle birleştiğinde düşünün.</span><span class="sxs-lookup"><span data-stu-id="45fba-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="45fba-128">gRPC, uygulamalar ve hizmetler arasında yüksek performanslı, düşük bant genişliğine bağlı iletişim sağlamak için HTTP/2 ve Protobuf ileti kodlama protokolü üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="45fba-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="45fba-129">.NET, Java, Python, Node.js, Go ve C++ gibi en popüler programlama dilleri ve platformlarında sunucu ve istemci kodu oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="45fba-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="45fba-130">ASP.NET Core 3.0'da gRPC için birinci sınıf desteği, .NET 4.x için mevcut gRPC araçları ve kütüphanelerinin yanı sıra, organizasyonlarında .NET Core'u benimsemek isteyen geliştirme ekipleri için WCF'ye mükemmel bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="45fba-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="45fba-131">Bu kılavuzu kimler kullanmalı?</span><span class="sxs-lookup"><span data-stu-id="45fba-131">Who should use this guide</span></span>

<span data-ttu-id="45fba-132">Bu kılavuz, .NET Framework veya .NET Core'da daha önce WCF kullanan ve uygulamalarını .NET Core 3.0 ve sonraki sürümler için modern bir RPC ortamına geçirmek isteyen geliştiriciler için yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="45fba-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="45fba-133">Daha genel olarak, .NET Core 3.0'a yükseltme veya yükseltme yi düşünüyorsanız ve yerleşik gRPC araçlarını kullanmak istiyorsanız, bu kılavuz da yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="45fba-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="45fba-134">Bu kılavuzu nasıl kullanabilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="45fba-134">How you can use this guide</span></span>

<span data-ttu-id="45fba-135">Bu, ASP.NET Core 3.0'da gRPC Hizmetleri oluşturmaya kısa bir giriştir ve özellikle wcf'ye benzer bir platform olarak atıfta bulunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45fba-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="45fba-136">Her kavramı WCF'nin eşdeğer özellikleriyle ilişkilendiren gRPC ilkelerini açıklar ve mevcut bir WCF uygulamasını gRPC'ye geçirmek için kılavuz sunar.</span><span class="sxs-lookup"><span data-stu-id="45fba-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="45fba-137">Ayrıca, WCF ile deneyime sahip olan ve yeni hizmetler oluşturmak için gRPC öğrenmek isteyen geliştiriciler için de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="45fba-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="45fba-138">Örnek uygulamaları kendi projeleriniz için bir şablon veya başvuru olarak kullanabilirsiniz ve kitaptan veya örneklerinden kodu kopyalayıp yeniden kullanmakta özgürüz.</span><span class="sxs-lookup"><span data-stu-id="45fba-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="45fba-139">Bu hususların ve fırsatların ortak bir şekilde anlaşılmasını sağlamaya yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="45fba-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="45fba-140">Herkesin ortak bir terimler ve temel ilkeler kümesinden çalışması mimari örüntülerin ve uygulamaların tutarlı bir şekilde uygulanmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="45fba-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="45fba-141">Başvurular</span><span class="sxs-lookup"><span data-stu-id="45fba-141">References</span></span>

- <span data-ttu-id="45fba-142">**gRPC web sitesi**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="45fba-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="45fba-143">**Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapmak**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="45fba-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="45fba-144">Sonraki</span><span class="sxs-lookup"><span data-stu-id="45fba-144">Next</span></span>](introduction.md)
