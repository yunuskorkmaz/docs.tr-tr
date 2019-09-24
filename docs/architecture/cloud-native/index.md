---
title: Azure için Cloud Native .NET uygulamaları tasarlama
description: Kapsayıcılardan, mikro hizmetlerden ve sunucusuz özelliklerden yararlanarak bulutta yerel uygulamalar oluşturmaya yönelik bir kılavuz.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 67e235b051702308d2455b2501bfb59a4317635b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214172"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="5ba4c-103">Azure için Cloud Native .NET uygulamaları tasarlama</span><span class="sxs-lookup"><span data-stu-id="5ba4c-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![kapak resmi](./media/cover.png)

<span data-ttu-id="5ba4c-105">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="5ba4c-105">PUBLISHED BY</span></span>

<span data-ttu-id="5ba4c-106">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="5ba4c-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="5ba4c-107">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="5ba4c-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="5ba4c-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="5ba4c-108">One Microsoft Way</span></span>

<span data-ttu-id="5ba4c-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="5ba4c-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="5ba4c-110">Telif hakkı © 2019 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="5ba4c-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="5ba4c-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-111">All rights reserved.</span></span> <span data-ttu-id="5ba4c-112">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="5ba4c-113">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="5ba4c-114">URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="5ba4c-115">Burada gösterilen bazı örnekler yalnızca gösterim amaçlıdır ve hayal ürünüdür.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="5ba4c-116">Hiçbir gerçek ilişkilendirme veya bağlantı amaçlanmaz veya çıkarsanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="5ba4c-117">Microsoft ve "ticari markalar" https://www.microsoft.com Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="5ba4c-118">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="5ba4c-119">Docker balina logosu, Docker, Inc 'nin tescilli ticari markasıdır. İzin tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="5ba4c-120">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="5ba4c-121">Düzenliyor</span><span class="sxs-lookup"><span data-stu-id="5ba4c-121">Authors:</span></span>

> <span data-ttu-id="5ba4c-122">**Steve "ardalış" Smith** -yazılım mimarı ve trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="5ba4c-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="5ba4c-123">**Ramiz Vettor** -Microsoft-asıl bulut sistem MIMARı/IP mimarı- [RobVettor.com](https://robvettor.com)</span><span class="sxs-lookup"><span data-stu-id="5ba4c-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)</span></span>

<span data-ttu-id="5ba4c-124">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="5ba4c-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="5ba4c-125">**Cesar de La Torre**, sorumlu Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5ba4c-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="5ba4c-126">**Hayvan anıl**, SR. Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5ba4c-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="5ba4c-127">Edit</span><span class="sxs-lookup"><span data-stu-id="5ba4c-127">Editors:</span></span>

> <span data-ttu-id="5ba4c-128">**Maira Wenzel**, SR. Content Developer, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="5ba4c-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="5ba4c-129">Bu kılavuzu kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="5ba4c-129">Who should use this guide</span></span>

<span data-ttu-id="5ba4c-130">Bu kılavuzun hedef kitlesi, bulut için tasarlanan uygulamaları oluşturmayı öğrenmede ilgilenen geliştiriciler, geliştirme liderleri ve mimarilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="5ba4c-131">İkincil hedef kitle, bulut Yerel bir yaklaşım kullanarak uygulamalarını oluşturmayı planlayan teknik karar mekanizmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="5ba4c-132">Bu Kılavuzu nasıl kullanabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="5ba4c-132">How you can use this guide</span></span>

<span data-ttu-id="5ba4c-133">Bu kılavuz, bulut Native 'i tanımlayarak başlar ve bulut Yerel ilkeleri ve teknolojileri kullanılarak oluşturulan bir başvuru uygulaması ile tanışın.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="5ba4c-134">Bu ilk iki bölüm dışında, kitabın geri kalanı, bulut Yerel uygulamalarının çoğunda ortak olan konulara odaklanan belirli bölümlere ayrılır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="5ba4c-135">Aşağıdaki gibi, buluta özgü yaklaşımlar hakkında bilgi edinmek için şu bölümlerden birine atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5ba4c-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="5ba4c-136">Veri ve veri erişimi</span><span class="sxs-lookup"><span data-stu-id="5ba4c-136">Data and data access</span></span>
- <span data-ttu-id="5ba4c-137">İletişim desenleri</span><span class="sxs-lookup"><span data-stu-id="5ba4c-137">Communication patterns</span></span>
- <span data-ttu-id="5ba4c-138">Ölçeklendirme ve ölçeklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="5ba4c-138">Scaling and scalability</span></span>
- <span data-ttu-id="5ba4c-139">Uygulama dayanıklılığı</span><span class="sxs-lookup"><span data-stu-id="5ba4c-139">Application resiliency</span></span>
- <span data-ttu-id="5ba4c-140">İzleme ve sistem durumu</span><span class="sxs-lookup"><span data-stu-id="5ba4c-140">Monitoring and health</span></span>
- <span data-ttu-id="5ba4c-141">Kimlik ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="5ba4c-141">Identity and security</span></span>
- <span data-ttu-id="5ba4c-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="5ba4c-142">DevOps</span></span>

<span data-ttu-id="5ba4c-143">Bu kılavuz hem PDF form hem de çevrimiçi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="5ba4c-144">Bu konu başlıklarının yaygın olarak anlaşılmasına yardımcı olmak için bu belgeyi veya çevrimiçi sürümünün bağlantısını ekibinize iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="5ba4c-145">Bu konuların çoğu, temel ilkelerin ve desenlerin tutarlı bir şekilde anlaşılmasından ve bu konularla ilgili kararlara dahil olan kararların dengelerinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="5ba4c-146">Bu belge ile olan amacınız, donatı ekiplerine ve liderlerine, uygulamalarının mimarisine, geliştirmeye ve barındırılmasına yönelik iyi bilinçli kararlar vermek için ihtiyaç duydukları bilgileri sunmaktır.</span><span class="sxs-lookup"><span data-stu-id="5ba4c-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="5ba4c-147">Next</span><span class="sxs-lookup"><span data-stu-id="5ba4c-147">Next</span></span>](introduction.md)
