---
title: Azure için Cloud Native .NET uygulamaları tasarlama
description: Kapsayıcılardan, mikro hizmetlerden ve sunucusuz özelliklerden yararlanarak bulutta yerel uygulamalar oluşturmaya yönelik bir kılavuz.
author: ardalis
ms.date: 05/13/2020
ms.openlocfilehash: b315f097b1584bd93f694c10f36ee7524d7e020a
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144389"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="008d1-103">Azure için Cloud Native .NET uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="008d1-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="008d1-105">**SÜRÜM v. 1.0**</span><span class="sxs-lookup"><span data-stu-id="008d1-105">**EDITION v.1.0**</span></span>

<span data-ttu-id="008d1-106">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="008d1-106">PUBLISHED BY</span></span>

<span data-ttu-id="008d1-107">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="008d1-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="008d1-108">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="008d1-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="008d1-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="008d1-109">One Microsoft Way</span></span>

<span data-ttu-id="008d1-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="008d1-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="008d1-111">Telif hakkı &copy; 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="008d1-111">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="008d1-112">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="008d1-112">All rights reserved.</span></span> <span data-ttu-id="008d1-113">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="008d1-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="008d1-114">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="008d1-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="008d1-115">URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="008d1-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="008d1-116">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="008d1-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="008d1-117">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="008d1-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="008d1-118">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="008d1-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="008d1-119">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="008d1-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="008d1-120">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="008d1-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="008d1-121">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="008d1-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="008d1-122">Düzenliyor</span><span class="sxs-lookup"><span data-stu-id="008d1-122">Authors:</span></span>

> <span data-ttu-id="008d1-123">**Ramiz Vettor**, sorumlu bulut sistemi MIMARı/IP mimarı- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="008d1-123">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="008d1-124">**Steve "ardalış" Smith**, yazılım mimarı ve Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="008d1-124">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="008d1-125">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="008d1-125">Participants and Reviewers:</span></span>

> <span data-ttu-id="008d1-126">**Cesar de La Torre**, sorumlu Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="008d1-126">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="008d1-127">**Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="008d1-127">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="008d1-128">**Jeremy Liksizlik**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="008d1-128">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="008d1-129">**Cecil Phillip**, üst düzey bulut Danışmanı, Microsoft</span><span class="sxs-lookup"><span data-stu-id="008d1-129">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="008d1-130">Edit</span><span class="sxs-lookup"><span data-stu-id="008d1-130">Editors:</span></span>

> <span data-ttu-id="008d1-131">**Maira Wenzel**, program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="008d1-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="008d1-132">Sürüm</span><span class="sxs-lookup"><span data-stu-id="008d1-132">Version</span></span>

<span data-ttu-id="008d1-133">Bu kılavuz, .NET Core 3,1 sürümüyle aynı "Wave" teknolojileri (Azure ve ek üçüncü taraf teknolojileri) ile ilgili birçok ek güncelleştirme ile birlikte **.net core 3,1** sürümünü kapsayacak şekilde yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="008d1-133">This guide has been written to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="008d1-134">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="008d1-134">Who should use this guide</span></span>

<span data-ttu-id="008d1-135">Bu kılavuzun hedef kitlesi, bulut için tasarlanan uygulamaları oluşturmayı öğrenmede ilgilenen geliştiriciler, geliştirme liderleri ve mimarilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="008d1-135">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="008d1-136">İkincil hedef kitle, bulut Yerel bir yaklaşım kullanarak uygulamalarını oluşturmayı planlayan teknik karar mekanizmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="008d1-136">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="008d1-137">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="008d1-137">How you can use this guide</span></span>

<span data-ttu-id="008d1-138">Bu kılavuz, bulut Native 'i tanımlayarak başlar ve bulut Yerel ilkeleri ve teknolojileri kullanılarak oluşturulan bir başvuru uygulaması ile tanışın.</span><span class="sxs-lookup"><span data-stu-id="008d1-138">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="008d1-139">Bu ilk iki bölüm dışında, kitabın geri kalanı, bulut Yerel uygulamalarının çoğunda ortak olan konulara odaklanan belirli bölümlere ayrılır.</span><span class="sxs-lookup"><span data-stu-id="008d1-139">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="008d1-140">Aşağıdaki gibi, buluta özgü yaklaşımlar hakkında bilgi edinmek için şu bölümlerden birine atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="008d1-140">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="008d1-141">Veri ve veri erişimi</span><span class="sxs-lookup"><span data-stu-id="008d1-141">Data and data access</span></span>
- <span data-ttu-id="008d1-142">Kimlik doğrulaması desenleri</span><span class="sxs-lookup"><span data-stu-id="008d1-142">Communication patterns</span></span>
- <span data-ttu-id="008d1-143">Ölçeklendirme ve ölçeklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="008d1-143">Scaling and scalability</span></span>
- <span data-ttu-id="008d1-144">Uygulama dayanıklılığı</span><span class="sxs-lookup"><span data-stu-id="008d1-144">Application resiliency</span></span>
- <span data-ttu-id="008d1-145">İzleme ve sistem durumu</span><span class="sxs-lookup"><span data-stu-id="008d1-145">Monitoring and health</span></span>
- <span data-ttu-id="008d1-146">Kimlik ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="008d1-146">Identity and security</span></span>
- <span data-ttu-id="008d1-147">DevOps</span><span class="sxs-lookup"><span data-stu-id="008d1-147">DevOps</span></span>

<span data-ttu-id="008d1-148">Bu kılavuz hem PDF form hem de çevrimiçi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="008d1-148">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="008d1-149">Bu konu başlıklarının yaygın olarak anlaşılmasına yardımcı olmak için bu belgeyi veya çevrimiçi sürümünün bağlantısını ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="008d1-149">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="008d1-150">Bu konuların çoğu, temel ilkelerin ve desenlerin tutarlı bir şekilde anlaşılmasından ve bu konularla ilgili kararlara dahil olan kararların dengelerinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="008d1-150">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="008d1-151">Bu belge ile olan amacınız, donatı ekiplerine ve liderlerine, uygulamalarının mimarisine, geliştirmeye ve barındırılmasına yönelik iyi bilinçli kararlar vermek için ihtiyaç duydukları bilgileri sunmaktır.</span><span class="sxs-lookup"><span data-stu-id="008d1-151">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="008d1-152">Geri bildiriminizi gönderin</span><span class="sxs-lookup"><span data-stu-id="008d1-152">Send your feedback</span></span>

<span data-ttu-id="008d1-153">Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı!</span><span class="sxs-lookup"><span data-stu-id="008d1-153">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="008d1-154">Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="008d1-154">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="008d1-155">Sonraki</span><span class="sxs-lookup"><span data-stu-id="008d1-155">Next</span></span>](introduction.md)
