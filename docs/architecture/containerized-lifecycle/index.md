---
title: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
description: Docker ve Microsoft platformu ve araçları ile Kapsayıcılı uygulamalar geliştirmeye ve dağıtmaya yönelik geliştirme ve dağıtım sürecine ileri düzey bir genel bakış alın.
ms.date: 07/30/2020
ms.openlocfilehash: d8055315b25f73d7b0b355026ab6b2c4767f9d89
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915163"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a>Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü

![Kitap kapağı](./media/devops-book-cover-large-we.png)

**Sürüm v 3.1** -ASP.NET Core 3,1 ' ye güncelleştirildi

Bu kılavuz, Microsoft platformu ve araçları kullanılarak Docker ile Kapsayıcılı ASP.NET Core uygulamalar geliştirmeye ve dağıtmaya yönelik genel bir genel bakıştır. Kılavuz, CI/CD işlem hatlarının yanı sıra Azure Container Registry (ACR) ve Azure Kubernetes Hizmetleri AKS ' i dağıtmak için Azure DevOps 'a yönelik yüksek düzeyde bir giriş içerir.

Düşük düzey, geliştirmeyle ilgili ayrıntılar için [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları](https://docs.microsoft.com/dotnet/architecture/microservices/) Kılavuzu ve BT ile ilgili başvuru uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers)için mimari görebilirsiniz.

## <a name="send-us-your-feedback"></a>Görüşlerinizi bize gönderin!

.NET 'teki Kapsayıcılı uygulamaların ve mikro hizmetlerin mimarisini anlamanıza yardımcı olması için bu kılavuzu yazdık. Kılavuz ve ilgili başvuru uygulaması geliştireceğiz, bu nedenle geri bildirimlerinize hoş geldiniz! Bu kılavuzun nasıl iyileştirilen hakkında açıklamalara sahipseniz, konusunda geri bildirimde bulunun <https://aka.ms/ebookfeedback> .

## <a name="credits"></a>Krediler

Yazar:

> **Cesar de La Torre**, SR. PM, .net ürün ekibi, Microsoft Corp.

Alım Düzenleyicisi:

> **Ida Patrick**

Geliştirme Düzenleyicisi:

> **Bob Russatı**, Microsoft 'Ta çözüm uzmanı
>
> [**Sekizlik yayımlama, Inc.**](http://www.octalpub.com/)

Düzenleme üretimi:

> [Dianne Russati](http://www.octalpub.com/)
>
> **Sekizlik yayımlama, Inc.**

Copyeditor:

> **Bob Russatı**, Microsoft 'Ta çözüm uzmanı

Katılımcılar ve gözden geçirenler:

> **Hayvan anıl**, SR. Program Yöneticisi, .NET ekibi, Microsoft
>
> **MIGUEL Veloso**, düz kavramlarda yazılım geliştirme mühendisi
>
> **Sumit Ghosh**, sorumlu danışman Neudesic

## <a name="copyright"></a>Telif Hakkı

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı &copy; 2020 Microsoft Corporation

All rights reserved. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

>[!div class="step-by-step"]
>[Sonraki](introduction-to-containers-and-docker.md)
