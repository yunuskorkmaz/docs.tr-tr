---
title: .NET 5 ile Windows 10 ' da masaüstü uygulamaları modernize etme
description: .NET 5 ile mevcut masaüstü uygulamalarını nasıl modernleştirin öğrenin
ms.date: 01/06/2021
ms.openlocfilehash: de8a451b0598b5eabd99028d377c161dace61623
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615716"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-5"></a><span data-ttu-id="602ce-103">.NET 5 ile Windows 10 ' da masaüstü uygulamaları modernize etme</span><span class="sxs-lookup"><span data-stu-id="602ce-103">Modernizing Desktop Apps on Windows 10 with .NET 5</span></span>

![Modernleştirin masaüstü uygulamaları e-kitap kapağını gösteren ekran görüntüsü.](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="602ce-105">**Sürüm v 1.0.1** -.NET 5 ' e güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="602ce-105">**EDITION v1.0.1** - Updated to .NET 5</span></span>

<span data-ttu-id="602ce-106">Kitap güncelleştirmeleri ve topluluk katkılarına yönelik [changelog](https://aka.ms/desktop-ebook-changelog) 'u inceleyin.</span><span class="sxs-lookup"><span data-stu-id="602ce-106">Refer [changelog](https://aka.ms/desktop-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="602ce-107">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="602ce-107">PUBLISHED BY</span></span>

<span data-ttu-id="602ce-108">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="602ce-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="602ce-109">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="602ce-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="602ce-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="602ce-110">One Microsoft Way</span></span>

<span data-ttu-id="602ce-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="602ce-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="602ce-112">Telif hakkı © 2021 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="602ce-112">Copyright © 2021 by Microsoft Corporation</span></span>

<span data-ttu-id="602ce-113">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="602ce-113">All rights reserved.</span></span> <span data-ttu-id="602ce-114">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="602ce-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="602ce-115">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="602ce-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="602ce-116">URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="602ce-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="602ce-117">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="602ce-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="602ce-118">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="602ce-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="602ce-119">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="602ce-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="602ce-120">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="602ce-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="602ce-121">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="602ce-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="602ce-122">Ortak Yazarlar:</span><span class="sxs-lookup"><span data-stu-id="602ce-122">Co-Authors:</span></span>

> <span data-ttu-id="602ce-123">**Kaya Gavrne sh**, program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-123">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="602ce-124">**Miguel Angel Castejón Dominguez**, yenilik mimarı, Kabel</span><span class="sxs-lookup"><span data-stu-id="602ce-124">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="602ce-125">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="602ce-125">Participants and reviewers:</span></span>

> <span data-ttu-id="602ce-126">**Maira Wenzel**, Kıdemli Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-126">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="602ce-127">**Andy de Gorge**, üst düzey içerik Geliştirici, .net docs ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-127">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="602ce-128">**MIGUEL rampa,** üst düzey Program Yöneticisi, Windows geliştirici platformu ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-128">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="602ce-129">**Adam Braden**, sorumlu Program Yöneticisi, Windows geliştirici platformu ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-129">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="602ce-130">**Ricardo Minguez Pablos**, üst düzey Program Yöneticisi, Azure IoT ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-130">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="602ce-131">**Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-131">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="602ce-132">**Beth massı**, Kıdemli Ürün Pazarlama Yöneticisi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-132">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="602ce-133">**Scott Hunter**, Iş ortağı Direktörü Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="602ce-133">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="602ce-134">**Marta Füentes Lara**, Kabel</span><span class="sxs-lookup"><span data-stu-id="602ce-134">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="602ce-135">**Raúl Fernández de kordobası**, Kabel</span><span class="sxs-lookup"><span data-stu-id="602ce-135">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="602ce-136">**Antonio Manuel Fernández Cantos**, Kabel</span><span class="sxs-lookup"><span data-stu-id="602ce-136">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="602ce-137">Giriş</span><span class="sxs-lookup"><span data-stu-id="602ce-137">Introduction</span></span>

<span data-ttu-id="602ce-138">Bu kitapta, mevcut masaüstü uygulamalarınızı modernleştirme yolu aracılığıyla taşımak ve en son çalışma zamanı, dil ve platform özelliklerini birleştirmek için benimseyen stratejiler vardır.</span><span class="sxs-lookup"><span data-stu-id="602ce-138">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="602ce-139">Her bir uygulama farklı olduğu için benzersiz tarif olmadığını ve bu nedenle gereksinimleriniz ve tercihleriniz olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="602ce-139">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="602ce-140">İyi haber, uygulamalarınıza yeni özellikler ve yetenekler eklemek için uygulayabileceğiniz yaygın yaklaşımlar vardır.</span><span class="sxs-lookup"><span data-stu-id="602ce-140">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="602ce-141">Bunlar, kodunuzun önemli değişikliklere gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="602ce-141">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="602ce-142">Bu kitapta, tüm bu özelliklerin arka planda nasıl çalıştığını açığa çıkarıyoruz ve uygulamalarına ait olan mekanonları açıklayacağız.</span><span class="sxs-lookup"><span data-stu-id="602ce-142">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="602ce-143">Üstelik, daha fazla şekilde gösterilen mevcut masaüstü uygulamalarını modernleştirmeye yönelik bazı yaygın senaryolar bulacaksınız. bu sayede, projelerinizi gelişmede daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="602ce-143">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="602ce-144">Microsoft 'un mevcut uygulamaları modernleştirmeye yönelik yaklaşımı, kendi özelleştirilmiş yolunu oluşturma esnekliği vermektir.</span><span class="sxs-lookup"><span data-stu-id="602ce-144">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="602ce-145">Bu kitapta açıklanan tüm modernleştirme stratejileri çoğunlukla bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="602ce-145">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="602ce-146">Uygulamanız için uygun olanları seçebilir ve sizin için önemli olmayan diğerlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="602ce-146">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="602ce-147">Diğer bir deyişle, uygulama gereksinimlerinizi en iyi şekilde karşılamak için stratejileri karıştırabilir ve eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="602ce-147">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="602ce-148">Kitabı kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="602ce-148">Who should use the book</span></span>

<span data-ttu-id="602ce-149">.NET ve Windows 10 ' un avantajlarından yararlanmak için mevcut Windows Forms ve WPF masaüstü uygulamalarını modernleştirin isteyen geliştiriciler ve çözüm mimarları için bu kitap.</span><span class="sxs-lookup"><span data-stu-id="602ce-149">This book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET and Windows 10.</span></span>

<span data-ttu-id="602ce-150">Bu kitabı, kurumsal mimarde veya mevcut masaüstü uygulamalarını güncelleştirme avantajlarına genel bakış isteyen bir geliştirme lideri veya Direktörü gibi teknik bir karar veren bir yardım için de bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="602ce-150">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="602ce-151">Kitabı kullanma</span><span class="sxs-lookup"><span data-stu-id="602ce-151">How to use the book</span></span>

<span data-ttu-id="602ce-152">Bu kitapta, "Neden", mevcut uygulamalarınızı nasıl modernleştirin isteyebileceğiniz ve NET ve MSIX kullanarak masaüstü uygulamalarınızı modernleştirin 'e alacağınız belirli avantajlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="602ce-152">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="602ce-153">Kitabın içeriği, genel bakış isteyen, ancak uygulama ve teknik, adım adım ayrıntılara odaklanmayı gerektirmeyen mimarlar ve teknik karar mekanizmaları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="602ce-153">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="602ce-154">Örnek uygulama kod parçacıkları ve ekran görüntüleri boyunca, örnek uygulamalar için tüm geçiş sürecini göstermek üzere Bölüm 5 ' le birlikte örnek uygulama kodu parçacıkları ve ekran görüntüleri sağlanır.</span><span class="sxs-lookup"><span data-stu-id="602ce-154">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="602ce-155">Bu kitabın kapsamıyor</span><span class="sxs-lookup"><span data-stu-id="602ce-155">What this book doesn't cover</span></span>

<span data-ttu-id="602ce-156">Bu kitap, kaldırma ve kaydırma senaryolarına odaklanan belirli senaryolar alt kümesini kapsamakta ve kodu yeniden yazma çabalarına gerek kalmadan modernize almanın avantajlarından yararlanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="602ce-156">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="602ce-157">Bu kitap, .NET ile modern uygulamalar geliştirmekten veya Windows Forms ve WPF ile çalışmaya başlama konusunda değildir.</span><span class="sxs-lookup"><span data-stu-id="602ce-157">This book isn't about developing modern applications with .NET from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="602ce-158">Masaüstü geliştirme için en son teknolojilerle mevcut masaüstü uygulamalarını nasıl güncelleştirekullanabileceğinizi ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="602ce-158">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="602ce-159">Bu kitapta kullanılan örnekler</span><span class="sxs-lookup"><span data-stu-id="602ce-159">Samples used in this book</span></span>

<span data-ttu-id="602ce-160">Bir modernleştirmeyi gerçekleştirmek için gerekli adımları vurgulamak için adlı örnek bir uygulama kullanacağız `eShopModernizing` .</span><span class="sxs-lookup"><span data-stu-id="602ce-160">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="602ce-161">Bu uygulamanın iki özelliği, Windows Forms ve WPF vardır ve her ikisinde de her ikisi de .NET 'e kadar modernleştirmeyi gerçekleştirme hakkında adım adım bir işlem göstereceğiz.</span><span class="sxs-lookup"><span data-stu-id="602ce-161">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET.</span></span>

<span data-ttu-id="602ce-162">Ayrıca, bu kitabın GitHub deposunda, adım adım öğreticiyi izlemeye karar verirseniz, ile ilgili bir işlem sonuçları bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="602ce-162">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="602ce-163">Geri bildiriminizi gönderin</span><span class="sxs-lookup"><span data-stu-id="602ce-163">Send your feedback</span></span>

<span data-ttu-id="602ce-164">Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı!</span><span class="sxs-lookup"><span data-stu-id="602ce-164">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="602ce-165">Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="602ce-165">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="602ce-166">Sonraki</span><span class="sxs-lookup"><span data-stu-id="602ce-166">Next</span></span>](why-modern-applications.md)
