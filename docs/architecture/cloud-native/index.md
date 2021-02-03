---
title: Azure için Cloud Native .NET uygulamaları tasarlama
description: Kapsayıcılardan, mikro hizmetlerden ve sunucusuz özelliklerden yararlanarak bulutta yerel uygulamalar oluşturmaya yönelik bir kılavuz.
author: ardalis
ms.date: 01/19/2021
ms.openlocfilehash: ad641517f9dc24aed9180cf6a092f4754739bceb
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506129"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="18cfa-103">Azure için Cloud Native .NET uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="18cfa-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="18cfa-105">**SÜRÜM v 1.0.2**</span><span class="sxs-lookup"><span data-stu-id="18cfa-105">**EDITION v1.0.2**</span></span>

<span data-ttu-id="18cfa-106">Kitap güncelleştirmeleri ve topluluk katkılarına yönelik [changelog](https://aka.ms/cn-ebook-changelog) 'u inceleyin.</span><span class="sxs-lookup"><span data-stu-id="18cfa-106">Refer [changelog](https://aka.ms/cn-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="18cfa-107">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="18cfa-107">PUBLISHED BY</span></span>

<span data-ttu-id="18cfa-108">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="18cfa-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="18cfa-109">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="18cfa-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="18cfa-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="18cfa-110">One Microsoft Way</span></span>

<span data-ttu-id="18cfa-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="18cfa-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="18cfa-112">Telif hakkı &copy; 2021 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="18cfa-112">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="18cfa-113">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="18cfa-113">All rights reserved.</span></span> <span data-ttu-id="18cfa-114">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="18cfa-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="18cfa-115">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="18cfa-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="18cfa-116">URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="18cfa-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="18cfa-117">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="18cfa-118">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="18cfa-119">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="18cfa-120">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="18cfa-121">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-121">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="18cfa-122">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="18cfa-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="18cfa-123">Düzenliyor</span><span class="sxs-lookup"><span data-stu-id="18cfa-123">Authors:</span></span>

> <span data-ttu-id="18cfa-124">**Ramiz Vettor**, sorumlu bulut sistemi MIMARı/IP mimarı- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="18cfa-124">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="18cfa-125">**Steve "ardalış" Smith**, yazılım mimarı ve Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="18cfa-125">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="18cfa-126">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="18cfa-126">Participants and Reviewers:</span></span>

> <span data-ttu-id="18cfa-127">**Cesar de La Torre**, sorumlu Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18cfa-127">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="18cfa-128">**Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18cfa-128">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="18cfa-129">**Jeremy Liksizlik**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18cfa-129">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="18cfa-130">**Cecil Phillip**, üst düzey bulut Danışmanı, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18cfa-130">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>
>
> <span data-ttu-id="18cfa-131">**Sumit Ghosh**, sorumlu danışman Neudesic</span><span class="sxs-lookup"><span data-stu-id="18cfa-131">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

<span data-ttu-id="18cfa-132">Edit</span><span class="sxs-lookup"><span data-stu-id="18cfa-132">Editors:</span></span>

> <span data-ttu-id="18cfa-133">**Maira Wenzel**, program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18cfa-133">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="18cfa-134">**David çam**, üst düzey içerik Geliştirici, .net belgeleri, Microsoft</span><span class="sxs-lookup"><span data-stu-id="18cfa-134">**David Pine**, Senior Content Developer, .NET docs, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="18cfa-135">Sürüm</span><span class="sxs-lookup"><span data-stu-id="18cfa-135">Version</span></span>

<span data-ttu-id="18cfa-136">Bu kılavuz, .NET 5 sürümü ile aynı "Wave" teknolojileri (Azure ve ek üçüncü taraf teknolojileri) ile ilgili birçok ek güncelleştirme ile birlikte **.NET 5** sürümünü kapsayacak şekilde yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-136">This guide has been written to cover **.NET 5** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET 5 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="18cfa-137">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="18cfa-137">Who should use this guide</span></span>

<span data-ttu-id="18cfa-138">Bu kılavuzun hedef kitlesi, bulut için tasarlanan uygulamaları oluşturmayı öğrenmede ilgilenen geliştiriciler, geliştirme liderleri ve mimarilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="18cfa-138">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="18cfa-139">İkincil hedef kitle, bulut Yerel bir yaklaşım kullanarak uygulamalarını oluşturmayı planlayan teknik karar mekanizmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-139">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="18cfa-140">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="18cfa-140">How you can use this guide</span></span>

<span data-ttu-id="18cfa-141">Bu kılavuz, bulut Native 'i tanımlayarak başlar ve bulut Yerel ilkeleri ve teknolojileri kullanılarak oluşturulan bir başvuru uygulaması ile tanışın.</span><span class="sxs-lookup"><span data-stu-id="18cfa-141">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="18cfa-142">Bu ilk iki bölüm dışında, kitabın geri kalanı, bulut Yerel uygulamalarının çoğunda ortak olan konulara odaklanan belirli bölümlere ayrılır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-142">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="18cfa-143">Aşağıdaki gibi, buluta özgü yaklaşımlar hakkında bilgi edinmek için şu bölümlerden birine atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="18cfa-143">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="18cfa-144">Veri ve veri erişimi</span><span class="sxs-lookup"><span data-stu-id="18cfa-144">Data and data access</span></span>
- <span data-ttu-id="18cfa-145">Kimlik doğrulaması desenleri</span><span class="sxs-lookup"><span data-stu-id="18cfa-145">Communication patterns</span></span>
- <span data-ttu-id="18cfa-146">Ölçeklendirme ve ölçeklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="18cfa-146">Scaling and scalability</span></span>
- <span data-ttu-id="18cfa-147">Uygulama dayanıklılığı</span><span class="sxs-lookup"><span data-stu-id="18cfa-147">Application resiliency</span></span>
- <span data-ttu-id="18cfa-148">İzleme ve sistem durumu</span><span class="sxs-lookup"><span data-stu-id="18cfa-148">Monitoring and health</span></span>
- <span data-ttu-id="18cfa-149">Kimlik ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="18cfa-149">Identity and security</span></span>
- <span data-ttu-id="18cfa-150">DevOps</span><span class="sxs-lookup"><span data-stu-id="18cfa-150">DevOps</span></span>

<span data-ttu-id="18cfa-151">Bu kılavuz hem [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) form hem de çevrimiçi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18cfa-151">This guide is available both in [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) form and online.</span></span> <span data-ttu-id="18cfa-152">Bu konu başlıklarının yaygın olarak anlaşılmasına yardımcı olmak için bu belgeyi veya çevrimiçi sürümünün bağlantısını ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="18cfa-152">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="18cfa-153">Bu konuların çoğu, temel ilkelerin ve desenlerin tutarlı bir şekilde anlaşılmasından ve bu konularla ilgili kararlara dahil olan kararların dengelerinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-153">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="18cfa-154">Bu belge ile olan amacınız, donatı ekiplerine ve liderlerine, uygulamalarının mimarisine, geliştirmeye ve barındırılmasına yönelik iyi bilinçli kararlar vermek için ihtiyaç duydukları bilgileri sunmaktır.</span><span class="sxs-lookup"><span data-stu-id="18cfa-154">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="18cfa-155">Geri bildiriminizi gönderin</span><span class="sxs-lookup"><span data-stu-id="18cfa-155">Send your feedback</span></span>

<span data-ttu-id="18cfa-156">Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı!</span><span class="sxs-lookup"><span data-stu-id="18cfa-156">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="18cfa-157">Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="18cfa-157">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="18cfa-158">Sonraki</span><span class="sxs-lookup"><span data-stu-id="18cfa-158">Next</span></span>](introduction.md)
