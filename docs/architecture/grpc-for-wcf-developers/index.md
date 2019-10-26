---
title: WCF geliştiricileri için ASP.NET Core gRPC-WCF geliştiricileri için gRPC
description: YAZıLACAK
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6a5b4f6d0b47a272f7a753e22bfd61b06202944a
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919372"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="8f089-103">WCF Geliştiricileri için ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="8f089-103">ASP.NET Core gRPC for WCF Developers</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="8f089-105">YAYıMLAYAN</span><span class="sxs-lookup"><span data-stu-id="8f089-105">PUBLISHED BY</span></span>

<span data-ttu-id="8f089-106">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="8f089-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="8f089-107">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="8f089-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="8f089-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="8f089-108">One Microsoft Way</span></span>

<span data-ttu-id="8f089-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="8f089-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="8f089-110">Telif hakkı © 2019 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8f089-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="8f089-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="8f089-111">All rights reserved.</span></span> <span data-ttu-id="8f089-112">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="8f089-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="8f089-113">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="8f089-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="8f089-114">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8f089-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="8f089-115">Burada gösterilen bazı örnekler yalnızca gösterim amaçlıdır ve hayal ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="8f089-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="8f089-116">Hiçbir gerçek ilişkilendirme veya bağlantı amaçlanmaz veya çıkarsanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f089-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="8f089-117">Microsoft ve "ticari markalar" Web sayfasındaki https://www.microsoft.com listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="8f089-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="8f089-118">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="8f089-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="8f089-119">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="8f089-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="8f089-120">Geliştirici</span><span class="sxs-lookup"><span data-stu-id="8f089-120">Author:</span></span>

> <span data-ttu-id="8f089-121">Yeniden **işaretle** -BT Teknik Müdürü- [görsel recode](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="8f089-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="8f089-122">**MDA bu,** teknik yazar</span><span class="sxs-lookup"><span data-stu-id="8f089-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="8f089-123">Edit</span><span class="sxs-lookup"><span data-stu-id="8f089-123">Editors:</span></span>

> <span data-ttu-id="8f089-124">**Maira Wenzel** -SR içerik geliştiricisi-Microsoft</span><span class="sxs-lookup"><span data-stu-id="8f089-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="8f089-125">Giriş</span><span class="sxs-lookup"><span data-stu-id="8f089-125">Introduction</span></span>

<span data-ttu-id="8f089-126">TODO</span><span class="sxs-lookup"><span data-stu-id="8f089-126">TODO</span></span>

## <a name="purpose"></a><span data-ttu-id="8f089-127">Amaç</span><span class="sxs-lookup"><span data-stu-id="8f089-127">Purpose</span></span>

<span data-ttu-id="8f089-128">TODO</span><span class="sxs-lookup"><span data-stu-id="8f089-128">TODO</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="8f089-129">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="8f089-129">Who should use this guide</span></span>

<span data-ttu-id="8f089-130">**BUNU GÜNCELLEŞTIR**</span><span class="sxs-lookup"><span data-stu-id="8f089-130">**UPDATE THIS**</span></span>

<span data-ttu-id="8f089-131">Bu kılavuzun hedef kitlesi, .NET Framework 4 ' te WCF çözümlerini, gRPC hizmetlerini kullanarak ASP.NET Core 3,0 ' ye geçirmeye ilgilenen WCF geliştiricileri, geliştirme müşteri adayları ve mimarlardır.</span><span class="sxs-lookup"><span data-stu-id="8f089-131">The audience for this guide is WCF developers, development leads, and architects who are interested in migrating WCF solutions on .NET Framework 4 and earlier to ASP.NET Core 3.0 using gRPC services.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="8f089-132">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="8f089-132">How you can use this guide</span></span>

<span data-ttu-id="8f089-133">**BUNU GÜNCELLEŞTIR**</span><span class="sxs-lookup"><span data-stu-id="8f089-133">**UPDATE THIS**</span></span>

<span data-ttu-id="8f089-134">Bu, WCF 'ye benzer bir platform olarak belirli bir başvuru ile ASP.NET Core 3,0 ' de gRPC hizmetleri oluşturmaya yönelik kısa bir giriş niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="8f089-134">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="8f089-135">GRPC 'nin ilkelerini açıklar, her bir kavramı WCF 'nin eşdeğer özellikleriyle birbirleriyle ilgili olarak, mevcut bir WCF uygulamasının gRPC 'ye geçirilmesi için rehberlik sunar.</span><span class="sxs-lookup"><span data-stu-id="8f089-135">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="8f089-136">Ayrıca, WCF deneyimi olan ve yeni hizmetler oluşturmak üzere gRPC 'yi öğrenmek isteyen geliştiriciler için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="8f089-136">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="8f089-137">Örnek uygulama, kendi projeleriniz için bir şablon veya başvuru olarak veya defterden veya örneklerinden kodu kopyalayıp yeniden kullandığınızda ücretsiz olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f089-137">The sample application can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="8f089-138">Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="8f089-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="8f089-139">Her bir gövdenin ortak bir terminoloji kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="8f089-139">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="8f089-140">Referanslar</span><span class="sxs-lookup"><span data-stu-id="8f089-140">References</span></span>

- <span data-ttu-id="8f089-141">**gRPC Web sitesi**</span><span class="sxs-lookup"><span data-stu-id="8f089-141">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="8f089-142">**Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**</span><span class="sxs-lookup"><span data-stu-id="8f089-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="8f089-143">Next</span><span class="sxs-lookup"><span data-stu-id="8f089-143">Next</span></span>](introduction.md)
