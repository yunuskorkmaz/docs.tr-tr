---
title: Azure için Cloud Native .NET Uygulamalarını Temel Alma
description: Azure'un kapsayıcıları, mikro hizmetler ve sunucusuz özelliklerinden yararlanan bulut tasimi uygulamaları oluşturma kılavuzu.
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 7f14a690d0153edc43f0ce7f4e91c9e9cd2c6858
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71696787"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="172da-103">Azure için Cloud Native .NET Uygulamalarını Temel Alma</span><span class="sxs-lookup"><span data-stu-id="172da-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![kapak resmi](./media/cover.png)

<span data-ttu-id="172da-105">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="172da-105">PUBLISHED BY</span></span>

<span data-ttu-id="172da-106">Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="172da-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="172da-107">Microsoft Corporation'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="172da-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="172da-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="172da-108">One Microsoft Way</span></span>

<span data-ttu-id="172da-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="172da-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="172da-110">Telif Hakkı © 2019 Microsoft Corporation tarafından</span><span class="sxs-lookup"><span data-stu-id="172da-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="172da-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="172da-111">All rights reserved.</span></span> <span data-ttu-id="172da-112">Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="172da-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="172da-113">Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="172da-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="172da-114">URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.</span><span class="sxs-lookup"><span data-stu-id="172da-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="172da-115">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="172da-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="172da-116">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="172da-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="172da-117">Microsoft ve "Ticari https://www.microsoft.com Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="172da-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="172da-118">Mac ve macOS, Apple Inc. şirketinin ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="172da-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="172da-119">Docker balina logosu, Docker, Inc. şirketinin izni yle kullanılan tescilli ticari markasıdır.</span><span class="sxs-lookup"><span data-stu-id="172da-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="172da-120">Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="172da-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="172da-121">Yazar:</span><span class="sxs-lookup"><span data-stu-id="172da-121">Authors:</span></span>

> <span data-ttu-id="172da-122">**Steve "ardalis" Smith** - Yazılım Mimarı ve Eğitmen - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="172da-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="172da-123">**Rob Vettor** - Microsoft - Baş Bulut Sistemi Mimarı/IP Mimarı - [RobVettor.com](https://robvettor.com)</span><span class="sxs-lookup"><span data-stu-id="172da-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)</span></span>

<span data-ttu-id="172da-124">Katılımcılar ve Gözden Geçirenler:</span><span class="sxs-lookup"><span data-stu-id="172da-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="172da-125">**Cesar De la Torre**, Baş Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="172da-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="172da-126">**Nish Anıl**, Sr. Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="172da-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="172da-127">Editörler:</span><span class="sxs-lookup"><span data-stu-id="172da-127">Editors:</span></span>

> <span data-ttu-id="172da-128">**Maira Wenzel**, Sr. İçerik Geliştirici, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="172da-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="172da-129">Bu kılavuzu kimler kullanmalı?</span><span class="sxs-lookup"><span data-stu-id="172da-129">Who should use this guide</span></span>

<span data-ttu-id="172da-130">Bu kılavuzun hedef kitlesi ağırlıklı olarak geliştiriciler, geliştirme yol gösterici ve bulut için tasarlanmış uygulamaların nasıl inşa edilebildiğini öğrenmek isteyen mimarlardır.</span><span class="sxs-lookup"><span data-stu-id="172da-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="172da-131">İkinci bir hedef kitle, bulut açi tabanlı bir yaklaşım kullanarak uygulamalarını oluşturup oluşturmayacağını seçmeyi planlayan teknik karar vericilerdir.</span><span class="sxs-lookup"><span data-stu-id="172da-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="172da-132">Bu kılavuzu nasıl kullanabilirsiniz?</span><span class="sxs-lookup"><span data-stu-id="172da-132">How you can use this guide</span></span>

<span data-ttu-id="172da-133">Bu kılavuz, bulut ayarı tanımlayan ve bulut adajilkeleri ve teknolojileri kullanılarak oluşturulmuş bir başvuru uygulaması sunarak başlar.</span><span class="sxs-lookup"><span data-stu-id="172da-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="172da-134">Bu ilk iki bölümün ötesinde, kitabın geri kalanı bulut tabanlı uygulamaların çoğunda ortak olan konulara odaklanan belirli bölümlere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="172da-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="172da-135">Bulut ait yaklaşımlar hakkında bilgi edinmek için bu bölümlerden herhangi biri için atlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="172da-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="172da-136">Veri ve veri erişimi</span><span class="sxs-lookup"><span data-stu-id="172da-136">Data and data access</span></span>
- <span data-ttu-id="172da-137">Kimlik doğrulaması desenleri</span><span class="sxs-lookup"><span data-stu-id="172da-137">Communication patterns</span></span>
- <span data-ttu-id="172da-138">Ölçekleme ve ölçeklenebilirlik</span><span class="sxs-lookup"><span data-stu-id="172da-138">Scaling and scalability</span></span>
- <span data-ttu-id="172da-139">Uygulama esnekliği</span><span class="sxs-lookup"><span data-stu-id="172da-139">Application resiliency</span></span>
- <span data-ttu-id="172da-140">İzleme ve sistem durumu</span><span class="sxs-lookup"><span data-stu-id="172da-140">Monitoring and health</span></span>
- <span data-ttu-id="172da-141">Kimlik ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="172da-141">Identity and security</span></span>
- <span data-ttu-id="172da-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="172da-142">DevOps</span></span>

<span data-ttu-id="172da-143">Bu kılavuz hem PDF formunda hem de çevrimiçi olarak mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="172da-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="172da-144">Bu konuların ortak bir şekilde anlaşılmasını sağlamaya yardımcı olmak için bu belgeyi veya çevrimiçi sürümüne bağlantılar iletmekten çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="172da-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="172da-145">Bu konuların çoğu, temel ilke ve örüntülerin tutarlı bir şekilde anlaşılmasının yanı sıra, bu konularla ilgili kararlarda yer alan dengelerden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="172da-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="172da-146">Bu belge ile amacımız, takımları ve liderlerini, uygulamalarının mimarisi, gelişimi ve barındırması için bilinçli kararlar almak için ihtiyaç duydukları bilgilerle donatmaktır.</span><span class="sxs-lookup"><span data-stu-id="172da-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="172da-147">Sonraki</span><span class="sxs-lookup"><span data-stu-id="172da-147">Next</span></span>](introduction.md)
