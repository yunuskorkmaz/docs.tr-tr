---
title: .NET geliştiricileri için dadpr
description: .NET geliştiricilerinin Microsoft 'un açık kaynaklı dağıtılmış uygulama çalışma zamanının tam gücünden yararlanmasını ve bu avantajlardan faydalamasını sağlar.
author: robvet
ms.date: 02/07/2021
ms.openlocfilehash: a9f1362d8e588790151f9b828f53de90565cacbb
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629670"
---
# <a name="dapr-for-net-developers"></a><span data-ttu-id="df2a8-103">.NET geliştiricileri için dadpr</span><span class="sxs-lookup"><span data-stu-id="df2a8-103">Dapr for .NET Developers</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="df2a8-105">**ÖNIZLEME SÜRÜMÜ**</span><span class="sxs-lookup"><span data-stu-id="df2a8-105">**PREVIEW EDITION**</span></span>

<span data-ttu-id="df2a8-106">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="df2a8-106">PUBLISHED BY</span></span>

<span data-ttu-id="df2a8-107">Microsoft Geliştirici bölmesi, .NET ve Azure ınubations ekipleri</span><span class="sxs-lookup"><span data-stu-id="df2a8-107">Microsoft Developer Division, .NET, and Azure Incubations teams</span></span>

<span data-ttu-id="df2a8-108">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="df2a8-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="df2a8-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="df2a8-109">One Microsoft Way</span></span>

<span data-ttu-id="df2a8-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="df2a8-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="df2a8-111">Telif hakkı &copy; 2021 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="df2a8-111">Copyright &copy; 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="df2a8-112">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="df2a8-112">All rights reserved.</span></span> <span data-ttu-id="df2a8-113">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="df2a8-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="df2a8-114">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="df2a8-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="df2a8-115">URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="df2a8-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="df2a8-116">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="df2a8-117">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="df2a8-118">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="df2a8-119">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="df2a8-120">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="df2a8-121">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="df2a8-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="df2a8-122">Düzenliyor</span><span class="sxs-lookup"><span data-stu-id="df2a8-122">Authors:</span></span>

> <span data-ttu-id="df2a8-123">**Ramiz Vettor**, sorumlu bulut çözümü mimarı- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="df2a8-123">**Rob Vettor**, Principal Cloud Solution Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="df2a8-124">**Sander Molenkamp**, sorumlu bulut mimarı/Microsoft MVP- [Sandermolenkamp.com](https://www.sandermolenkamp.com), [Info desteği](https://www.infosupport.com/en/)</span><span class="sxs-lookup"><span data-stu-id="df2a8-124">**Sander Molenkamp**, Principal Cloud Architect/Microsoft MVP - [sandermolenkamp.com](https://www.sandermolenkamp.com), [Info Support](https://www.infosupport.com/en/)</span></span>
>
> <span data-ttu-id="df2a8-125">**Edwin Van Wijk**, Principal Solution mimarı/Microsoft MVP- [Defaultconstructor.com](https://defaultconstructor.com), [Info desteği](https://www.infosupport.com/en/)</span><span class="sxs-lookup"><span data-stu-id="df2a8-125">**Edwin van Wijk**, Principal Solution Architect/Microsoft MVP - [defaultconstructor.com](https://defaultconstructor.com), [Info Support](https://www.infosupport.com/en/)</span></span>

<span data-ttu-id="df2a8-126">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="df2a8-126">Participants and Reviewers:</span></span>

> <span data-ttu-id="df2a8-127">**Mark Russinovich**, Azure CTO ve teknik bir, Azure Office CTO, Microsoft</span><span class="sxs-lookup"><span data-stu-id="df2a8-127">**Mark Russinovich**, Azure CTO and Technical Fellow, Azure Office of CTO, Microsoft</span></span>
>
> <span data-ttu-id="df2a8-128">**Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="df2a8-128">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="df2a8-129">**Mark Fussell**, Principal program Manager, Azure ınubations, Microsoft</span><span class="sxs-lookup"><span data-stu-id="df2a8-129">**Mark Fussell**, Principal Program Manager, Azure Incubations, Microsoft</span></span>
>
> <span data-ttu-id="df2a8-130">**Yaron Schneider**, sorumlu yazılım mühendisi, Azure ınubations, Microsoft</span><span class="sxs-lookup"><span data-stu-id="df2a8-130">**Yaron Schneider**, Principal Software Engineer, Azure Incubations, Microsoft</span></span>
>
> <span data-ttu-id="df2a8-131">**Ori Zohar**, üst düzey Program Yöneticisi, Azure ınubations, Microsoft</span><span class="sxs-lookup"><span data-stu-id="df2a8-131">**Ori Zohar**, Senior Program Manager, Azure Incubations, Microsoft</span></span>

<span data-ttu-id="df2a8-132">Edit</span><span class="sxs-lookup"><span data-stu-id="df2a8-132">Editors:</span></span>

> <span data-ttu-id="df2a8-133">**David çam**, üst düzey içerik Geliştirici, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="df2a8-133">**David Pine**, Senior Content Developer, .NET team, Microsoft</span></span>

> <span data-ttu-id="df2a8-134">**Maira Wenzel**, program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="df2a8-134">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="df2a8-135">Sürüm</span><span class="sxs-lookup"><span data-stu-id="df2a8-135">Version</span></span>

<span data-ttu-id="df2a8-136">Bu kılavuz, **Davpr 1,0** sürümünü kapsayacak şekilde yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-136">This guide has been written to cover the **Dapr 1.0** version.</span></span> <span data-ttu-id="df2a8-137">.NET Core örnekleri, **.net core 3,1**' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-137">.NET Core samples are based on **.NET Core 3.1**.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="df2a8-138">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="df2a8-138">Who should use this guide</span></span>

<span data-ttu-id="df2a8-139">Bu kılavuzun hedef kitlesi, bulut için tasarlanan uygulamaları oluşturmayı öğrenmede ilgilenen geliştiriciler, geliştirme liderleri ve mimarilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="df2a8-139">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="df2a8-140">İkincil hedef kitle, bulut Yerel bir yaklaşım kullanarak uygulamalarını oluşturmayı planlayan teknik karar mekanizmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-140">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="df2a8-141">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="df2a8-141">How you can use this guide</span></span>

<span data-ttu-id="df2a8-142">Bu kılavuz hem [PDF](https://aka.ms/dapr-ebook) form hem de çevrimiçi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df2a8-142">This guide is available both in [PDF](https://aka.ms/dapr-ebook) form and online.</span></span> <span data-ttu-id="df2a8-143">Bu konu başlıklarının yaygın olarak anlaşılmasına yardımcı olmak için bu belgeyi veya çevrimiçi sürümünün bağlantısını ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="df2a8-143">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="df2a8-144">Bu konuların çoğu, temel ilkelerin ve desenlerin tutarlı bir şekilde anlaşılmasından ve bu konularla ilgili kararlara dahil olan kararların dengelerinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-144">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="df2a8-145">Bu belge ile olan amacınız, donatı ekiplerine ve liderlerine, uygulamalarının mimarisine, geliştirmeye ve barındırılmasına yönelik iyi bilinçli kararlar vermek için ihtiyaç duydukları bilgileri sunmaktır.</span><span class="sxs-lookup"><span data-stu-id="df2a8-145">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="df2a8-146">Geri bildiriminizi gönderin</span><span class="sxs-lookup"><span data-stu-id="df2a8-146">Send your feedback</span></span>

<span data-ttu-id="df2a8-147">Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı!</span><span class="sxs-lookup"><span data-stu-id="df2a8-147">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="df2a8-148">Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="df2a8-148">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="df2a8-149">Sonraki</span><span class="sxs-lookup"><span data-stu-id="df2a8-149">Next</span></span>](foreword.md)
