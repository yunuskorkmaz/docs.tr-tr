---
title: Mevcut ASP.NET uygulamalarını .NET Core 'a taşıma
description: ASP.NET MVC ve Web API uygulamalarını ASP.NET Core dönüştürmeye yönelik ücretsiz kılavuz.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 848f0e9533a65b59055853f1d502307abb69118c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105951"
---
# <a name="porting-existing-aspnet-apps-to-net-core"></a>Mevcut ASP.NET uygulamalarını .NET Core 'a taşıma

![kapak resmi](./media/index/porting-existing-aspnet-apps.png)

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı &copy; 2020 Microsoft Corporation

All rights reserved. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde çoğaltılamaz.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Düzenliyor

> **Steve "ardalış" Smith**, yazılım mimarı ve Trainer- [Ardalis.com](https://ardalis.com)

Katılımcılar ve gözden geçirenler:

> **Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft

> **Mike Rousos**, sorumlu yazılım mühendisi, .NET ekibi, Microsoft

> **Scott Ade**, üst düzey içerik Geliştirici, .NET ekibi, Microsoft

> **David çam**, üst düzey içerik Geliştirici, .NET ekibi, Microsoft

## <a name="version"></a>Sürüm

Bu kılavuzda .NET Core 3,1 sürümü ile aynı teknoloji "Wave" (yani Azure ve diğer üçüncü taraf teknolojileri) coinciding ile ilişkili **.net core 3,1** ve güncelleştirmeleri ele alınmaktadır. .NET Core 3,1 ' den .NET 5,0 ' e (sonraki sürüm) güncelleştirme oldukça basittir ve kesinlikle .NET Framework, .NET Core 'a kadar çok daha az çaba gerektirir. .NET Framework 4. x ' ten .NET 5,0 ' e geçiş, .NET Core 3,1 ' e geçirmeye benzer. Daha fazla bilgi için bkz. [doğru .NET Core sürümünü seçme](choose-net-core-version.md).

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

Bu kılavuzun hedef kitlesi, ASP.NET MVC ve Web API 'SI (.NET Framework 4. x) için yazılmış mevcut uygulamalarını .NET Core 'a geçirmeye ilgilenen geliştiriciler, geliştirme müşteri adayları ve mimarlardır. ASP.NET Web Forms geliştiriciler bu kılavuzdan faydalanır, ancak [ASP.NET Web Forms geliştiricileri](../blazor-for-web-forms-developers/index.md) e-book için Blazor ' i de okumalı.

İkincil bir hedef kitle, uygulamalarını .NET Core 'a ne zaman taşıyacağınız teknik karar verme mekanizmalarıdır.

Bu kitabın hedef kitlesi, ASP.NET MVC ve Web API 'sinde çalışan büyük, mevcut uygulamalarla .NET geliştiricidir. ASP.NET Web Forms oluşturulan uygulamalar bu kitabın odaklanarak .NET Framework ve .NET Core 'un karşılaştırıldığı bilgilerin büyük bir bölümü hala ilgili olabilir.

## <a name="how-you-can-use-this-guide"></a>Bu Kılavuzu nasıl kullanabileceğiniz

Birçok okuyucunun yapması beklendiğinden, bu kitabı doğrudan okuyabilirsiniz. Bu kitapta, uygulamanızı her seferinde bağlantı noktası yapmanız gerekip gerekmediğini göz önünde bulundurmanız gerekir. Bu içerik, .NET Framework ve .NET Core arasındaki mimari farklılığı izler. Buradan, büyük bir çözümü zamana göre geçirme ve gerçek bir uygulamanın bağlantı noktası oluşturma stratejilerini öğreneceksiniz. Daha sonra kitap, kullanıcılara tek bir uygulama olarak görünirken farklı uygulamalar çalıştırma gereksinimini karşılayan dağıtım senaryolarını içerir. Kitap, ASP.NET MVC 'den ASP.NET Core 'e geçirilmiş gerçek uygulamaları açıklayan iki örnek olay incelemesi ile sonlanır.

İlk bölümde başlatmayı tercih etmeksizin, belirli kavramlar hakkında bilgi edinmek için şu bölümlerden birine başvurabilirsiniz:

- [Mimari farklılıklar](architectural-differences.md)
- [Büyük çözümleri geçirme](migrate-large-solutions.md)
- [Örnek geçiş](example-migration-eshop.md)
- [Dağıtım senaryoları](deployment-scenarios.md)

Bu kılavuz hem [PDF form](https://aka.ms/aspnet-porting-ebook) hem de çevrimiçi olarak kullanılabilir. Bu kavramların yaygın olarak anlaşılmasından emin olmak için bu belgeyi veya çevrimiçi sürümüne olan bağlantıları ekibinize iletmekten çekinmeyin.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı! Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Sonraki](introduction.md)
