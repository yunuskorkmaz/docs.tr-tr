---
title: .NET Core 3,1 ile Windows 10 ' da masaüstü uygulamaları modernize etme
description: .NET Core 3,1 ile mevcut masaüstü uygulamalarını nasıl modernleştirin öğrenin
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423238"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a><span data-ttu-id="f3297-103">.NET Core 3,1 ile Windows 10 ' da masaüstü uygulamaları modernize etme</span><span class="sxs-lookup"><span data-stu-id="f3297-103">Modernizing Desktop Apps on Windows 10 with .NET Core 3.1</span></span>

![Modernleştirin masaüstü uygulamaları e-kitap kapağını gösteren ekran görüntüsü.](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="f3297-105">YAYIMLAYAN</span><span class="sxs-lookup"><span data-stu-id="f3297-105">PUBLISHED BY</span></span>

<span data-ttu-id="f3297-106">Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri</span><span class="sxs-lookup"><span data-stu-id="f3297-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="f3297-107">Microsoft Corporation 'ın bir bölümü</span><span class="sxs-lookup"><span data-stu-id="f3297-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="f3297-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="f3297-108">One Microsoft Way</span></span>

<span data-ttu-id="f3297-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="f3297-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="f3297-110">Telif hakkı © 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="f3297-110">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="f3297-111">Tüm hakları saklıdır.</span><span class="sxs-lookup"><span data-stu-id="f3297-111">All rights reserved.</span></span> <span data-ttu-id="f3297-112">Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="f3297-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="f3297-113">Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="f3297-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="f3297-114">Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f3297-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="f3297-115">Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır.</span><span class="sxs-lookup"><span data-stu-id="f3297-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="f3297-116">Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3297-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="f3297-117">Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="f3297-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="f3297-118">Mac ve macOS, Apple Inc. ' in ticari markalarıdır.</span><span class="sxs-lookup"><span data-stu-id="f3297-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="f3297-119">Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.</span><span class="sxs-lookup"><span data-stu-id="f3297-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="f3297-120">Ortak Yazarlar:</span><span class="sxs-lookup"><span data-stu-id="f3297-120">Co-Authors:</span></span>

> <span data-ttu-id="f3297-121">**Kaya Gavrne sh**, program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-121">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="f3297-122">**Miguel Angel Castejón Dominguez**, yenilik mimarı, Kabel</span><span class="sxs-lookup"><span data-stu-id="f3297-122">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="f3297-123">Katılımcılar ve gözden geçirenler:</span><span class="sxs-lookup"><span data-stu-id="f3297-123">Participants and reviewers:</span></span>

> <span data-ttu-id="f3297-124">**Maira Wenzel**, Kıdemli Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-124">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="f3297-125">**Andy de Gorge**, üst düzey içerik Geliştirici, .net docs ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-125">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="f3297-126">**MIGUEL rampa,** üst düzey Program Yöneticisi, Windows geliştirici platformu ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-126">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="f3297-127">**Adam Braden**, sorumlu Program Yöneticisi, Windows geliştirici platformu ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-127">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="f3297-128">**Ricardo Minguez Pablos**, üst düzey Program Yöneticisi, Azure IoT ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-128">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="f3297-129">**Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-129">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="f3297-130">**Beth massı**, Kıdemli Ürün Pazarlama Yöneticisi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-130">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="f3297-131">**Scott Hunter**, Iş ortağı Direktörü Program Yöneticisi, .NET ekibi, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3297-131">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="f3297-132">**Marta Füentes Lara**, Kabel</span><span class="sxs-lookup"><span data-stu-id="f3297-132">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="f3297-133">**Raúl Fernández de kordobası**, Kabel</span><span class="sxs-lookup"><span data-stu-id="f3297-133">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="f3297-134">**Antonio Manuel Fernández Cantos**, Kabel</span><span class="sxs-lookup"><span data-stu-id="f3297-134">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="f3297-135">Giriş</span><span class="sxs-lookup"><span data-stu-id="f3297-135">Introduction</span></span>

<span data-ttu-id="f3297-136">Bu kitapta, mevcut masaüstü uygulamalarınızı modernleştirme yolu aracılığıyla taşımak ve en son çalışma zamanı, dil ve platform özelliklerini birleştirmek için benimseyen stratejiler vardır.</span><span class="sxs-lookup"><span data-stu-id="f3297-136">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="f3297-137">Her bir uygulama farklı olduğu için benzersiz tarif olmadığını ve bu nedenle gereksinimleriniz ve tercihleriniz olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f3297-137">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="f3297-138">İyi haber, uygulamalarınıza yeni özellikler ve yetenekler eklemek için uygulayabileceğiniz yaygın yaklaşımlar vardır.</span><span class="sxs-lookup"><span data-stu-id="f3297-138">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="f3297-139">Bunlar, kodunuzun önemli değişikliklere gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="f3297-139">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="f3297-140">Bu kitapta, tüm bu özelliklerin arka planda nasıl çalıştığını açığa çıkarıyoruz ve uygulamalarına ait olan mekanonları açıklayacağız.</span><span class="sxs-lookup"><span data-stu-id="f3297-140">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="f3297-141">Üstelik, daha fazla şekilde gösterilen mevcut masaüstü uygulamalarını modernleştirmeye yönelik bazı yaygın senaryolar bulacaksınız. bu sayede, projelerinizi gelişmede daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3297-141">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="f3297-142">Microsoft 'un mevcut uygulamaları modernleştirmeye yönelik yaklaşımı, kendi özelleştirilmiş yolunu oluşturma esnekliği vermektir.</span><span class="sxs-lookup"><span data-stu-id="f3297-142">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="f3297-143">Bu kitapta açıklanan tüm modernleştirme stratejileri çoğunlukla bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="f3297-143">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="f3297-144">Uygulamanız için uygun olanları seçebilir ve sizin için önemli olmayan diğerlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3297-144">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="f3297-145">Diğer bir deyişle, uygulama gereksinimlerinizi en iyi şekilde karşılamak için stratejileri karıştırabilir ve eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3297-145">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="f3297-146">Kitabı kimler kullanmalıdır?</span><span class="sxs-lookup"><span data-stu-id="f3297-146">Who should use the book</span></span>

<span data-ttu-id="f3297-147">.NET Core ve Windows 10 ' un avantajlarından yararlanmak için mevcut Windows Forms ve WPF masaüstü uygulamalarını modernleştirin isteyen geliştiriciler ve çözüm mimarları için bu kitabı yazdık.</span><span class="sxs-lookup"><span data-stu-id="f3297-147">We wrote this book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET Core and Windows 10.</span></span>

<span data-ttu-id="f3297-148">Bu kitabı, kurumsal mimarde veya mevcut masaüstü uygulamalarını güncelleştirme avantajlarına genel bakış isteyen bir geliştirme lideri veya Direktörü gibi teknik bir karar veren bir yardım için de bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3297-148">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="f3297-149">Kitabı kullanma</span><span class="sxs-lookup"><span data-stu-id="f3297-149">How to use the book</span></span>

<span data-ttu-id="f3297-150">Bu kitapta, "Neden", mevcut uygulamalarınızı nasıl modernleştirin isteyebileceğiniz ve NET Core 3,1 ve MSIX kullanarak masaüstü uygulamalarınızı modernleştirin 'e alacağınız belirli avantajlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3297-150">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET Core 3.1 and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="f3297-151">Kitabın içeriği, genel bakış isteyen, ancak uygulama ve teknik, adım adım ayrıntılara odaklanmayı gerektirmeyen mimarlar ve teknik karar mekanizmaları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f3297-151">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="f3297-152">Örnek uygulama kod parçacıkları ve ekran görüntüleri boyunca, örnek uygulamalar için tüm geçiş sürecini göstermek üzere Bölüm 5 ' le birlikte örnek uygulama kodu parçacıkları ve ekran görüntüleri sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f3297-152">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="f3297-153">Bu kitabın kapsamıyor</span><span class="sxs-lookup"><span data-stu-id="f3297-153">What this book doesn't cover</span></span>

<span data-ttu-id="f3297-154">Bu kitap, kaldırma ve kaydırma senaryolarına odaklanan belirli senaryolar alt kümesini kapsamakta ve kodu yeniden yazma çabalarına gerek kalmadan modernize almanın avantajlarından yararlanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3297-154">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="f3297-155">Bu kitapta, .NET Core ile modern uygulamalar geliştirilirken veya Windows Forms ve WPF ile çalışmaya başlama hakkında bilgi verilmez.</span><span class="sxs-lookup"><span data-stu-id="f3297-155">This book isn't about developing modern applications with .NET Core from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="f3297-156">Masaüstü geliştirme için en son teknolojilerle mevcut masaüstü uygulamalarını nasıl güncelleştirekullanabileceğinizi ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3297-156">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="f3297-157">Bu kitapta kullanılan örnekler</span><span class="sxs-lookup"><span data-stu-id="f3297-157">Samples used in this book</span></span>

<span data-ttu-id="f3297-158">Bir modernleştirmeyi gerçekleştirmek için gerekli adımları vurgulamak için adlı örnek bir uygulama kullanacağız `eShopModernizing` .</span><span class="sxs-lookup"><span data-stu-id="f3297-158">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="f3297-159">Bu uygulamanın iki özelliği, Windows Forms ve WPF vardır ve her ikisinde de her ikisi de .NET Core 'a nasıl gerçekleştirileceği konusunda adım adım bir işlem göstereceğiz.</span><span class="sxs-lookup"><span data-stu-id="f3297-159">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET Core.</span></span>

<span data-ttu-id="f3297-160">Ayrıca, bu kitabın GitHub deposunda, adım adım öğreticiyi izlemeye karar verirseniz, ile ilgili bir işlem sonuçları bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="f3297-160">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="f3297-161">Geri bildiriminizi gönderin</span><span class="sxs-lookup"><span data-stu-id="f3297-161">Send your feedback</span></span>

<span data-ttu-id="f3297-162">Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı!</span><span class="sxs-lookup"><span data-stu-id="f3297-162">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="f3297-163">Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="f3297-163">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="f3297-164">Sonraki</span><span class="sxs-lookup"><span data-stu-id="f3297-164">Next</span></span>](why-modern-applications.md)
