---
title: Azure için Cloud Native .NET uygulamaları tasarlama
description: Kapsayıcılardan, mikro hizmetlerden ve sunucusuz özelliklerden yararlanarak bulutta yerel uygulamalar oluşturmaya yönelik bir kılavuz.
author: ardalis
ms.date: 04/23/2020
ms.openlocfilehash: 24d5c75fc5d2e5623892e8f83daea52553d13765
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507396"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="1ffc0-103">Azure için Cloud Native .NET uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="1ffc0-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![kapak resmi](./media/cover.png)

<span data-ttu-id="1ffc0-105">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="1ffc0-105">PUBLISHED BY</span></span>

<span data-ttu-id="1ffc0-106">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="1ffc0-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="1ffc0-107">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="1ffc0-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="1ffc0-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="1ffc0-108">One Microsoft Way</span></span>

<span data-ttu-id="1ffc0-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="1ffc0-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="1ffc0-110">Telif &copy; hakkı 2019 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1ffc0-110">Copyright &copy; 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="1ffc0-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-111">All rights reserved.</span></span> <span data-ttu-id="1ffc0-112">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="1ffc0-113">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="1ffc0-114">URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="1ffc0-115">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="1ffc0-116">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="1ffc0-117">Microsoft ve "ticari markalar" https://www.microsoft.com Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="1ffc0-118">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="1ffc0-119">Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="1ffc0-120">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="1ffc0-121">Düzenliyor</span><span class="sxs-lookup"><span data-stu-id="1ffc0-121">Authors:</span></span>

> <span data-ttu-id="1ffc0-122">**Ramiz Vettor**, sorumlu bulut sistemi MIMARı/IP mimarı- [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="1ffc0-122">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="1ffc0-123">**Steve "ardalış" Smith**, yazılım mimarı ve Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="1ffc0-123">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="1ffc0-124">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="1ffc0-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="1ffc0-125">**Cesar de La Torre**, sorumlu Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="1ffc0-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="1ffc0-126">**Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="1ffc0-126">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="1ffc0-127">**Jeremy Liksizlik**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="1ffc0-127">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="1ffc0-128">**Cecil Phillip**, üst düzey bulut Danışmanı, Microsoft</span><span class="sxs-lookup"><span data-stu-id="1ffc0-128">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="1ffc0-129">EShopOnContainers hakkında daha fazla bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="1ffc0-129">Learn more about eShopOnContainers</span></span>

<span data-ttu-id="1ffc0-130">Edit</span><span class="sxs-lookup"><span data-stu-id="1ffc0-130">Editors:</span></span>

> <span data-ttu-id="1ffc0-131">**Maira Wenzel**, program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="1ffc0-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="1ffc0-132">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="1ffc0-132">Who should use this guide</span></span>

<span data-ttu-id="1ffc0-133">Bu kılavuzun hedef kitlesi, bulut için tasarlanan uygulamaları oluşturmayı öğrenmede ilgilenen geliştiriciler, geliştirme liderleri ve mimarilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-133">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="1ffc0-134">İkincil hedef kitle, bulut Yerel bir yaklaşım kullanarak uygulamalarını oluşturmayı planlayan teknik karar mekanizmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-134">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="1ffc0-135">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="1ffc0-135">How you can use this guide</span></span>

<span data-ttu-id="1ffc0-136">Bu kılavuz, bulut Native 'i tanımlayarak başlar ve bulut Yerel ilkeleri ve teknolojileri kullanılarak oluşturulan bir başvuru uygulaması ile tanışın.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-136">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="1ffc0-137">Bu ilk iki bölüm dışında, kitabın geri kalanı, bulut Yerel uygulamalarının çoğunda ortak olan konulara odaklanan belirli bölümlere ayrılır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-137">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="1ffc0-138">Aşağıdaki gibi, buluta özgü yaklaşımlar hakkında bilgi edinmek için şu bölümlerden birine atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1ffc0-138">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="1ffc0-139">Veri ve veri erişimi</span><span class="sxs-lookup"><span data-stu-id="1ffc0-139">Data and data access</span></span>
- <span data-ttu-id="1ffc0-140">Kimlik doğrulaması desenleri</span><span class="sxs-lookup"><span data-stu-id="1ffc0-140">Communication patterns</span></span>
- <span data-ttu-id="1ffc0-141">Ölçeklendirme ve ölçeklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="1ffc0-141">Scaling and scalability</span></span>
- <span data-ttu-id="1ffc0-142">Uygulama dayanıklılığı</span><span class="sxs-lookup"><span data-stu-id="1ffc0-142">Application resiliency</span></span>
- <span data-ttu-id="1ffc0-143">İzleme ve sistem durumu</span><span class="sxs-lookup"><span data-stu-id="1ffc0-143">Monitoring and health</span></span>
- <span data-ttu-id="1ffc0-144">Kimlik ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="1ffc0-144">Identity and security</span></span>
- <span data-ttu-id="1ffc0-145">DevOps</span><span class="sxs-lookup"><span data-stu-id="1ffc0-145">DevOps</span></span>

<span data-ttu-id="1ffc0-146">Bu kılavuz hem PDF form hem de çevrimiçi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-146">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="1ffc0-147">Bu konu başlıklarının yaygın olarak anlaşılmasına yardımcı olmak için bu belgeyi veya çevrimiçi sürümünün bağlantısını ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-147">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="1ffc0-148">Bu konuların çoğu, temel ilkelerin ve desenlerin tutarlı bir şekilde anlaşılmasından ve bu konularla ilgili kararlara dahil olan kararların dengelerinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-148">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="1ffc0-149">Bu belge ile olan amacınız, donatı ekiplerine ve liderlerine, uygulamalarının mimarisine, geliştirmeye ve barındırılmasına yönelik iyi bilinçli kararlar vermek için ihtiyaç duydukları bilgileri sunmaktır.</span><span class="sxs-lookup"><span data-stu-id="1ffc0-149">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="1ffc0-150">Sonraki</span><span class="sxs-lookup"><span data-stu-id="1ffc0-150">Next</span></span>](introduction.md)
