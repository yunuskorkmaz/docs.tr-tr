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
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a>.NET Core 3,1 ile Windows 10 ' da masaüstü uygulamaları modernize etme

![Modernleştirin masaüstü uygulamaları e-kitap kapağını gösteren ekran görüntüsü.](./media/modernizing-existing-desktop-apps-ebook-cover.png)

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2020 Microsoft Corporation

Tüm hakları saklıdır. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Ortak Yazarlar:

> **Kaya Gavrne sh**, program Yöneticisi, .NET ekibi, Microsoft

> **Miguel Angel Castejón Dominguez**, yenilik mimarı, Kabel

Katılımcılar ve gözden geçirenler:

> **Maira Wenzel**, Kıdemli Program Yöneticisi, .NET ekibi, Microsoft

> **Andy de Gorge**, üst düzey içerik Geliştirici, .net docs ekibi, Microsoft

> **MIGUEL rampa,** üst düzey Program Yöneticisi, Windows geliştirici platformu ekibi, Microsoft

> **Adam Braden**, sorumlu Program Yöneticisi, Windows geliştirici platformu ekibi, Microsoft

> **Ricardo Minguez Pablos**, üst düzey Program Yöneticisi, Azure IoT ekibi, Microsoft

> **Hayvan anıl**, üst düzey Program Yöneticisi, .NET ekibi, Microsoft

> **Beth massı**, Kıdemli Ürün Pazarlama Yöneticisi, Microsoft

> **Scott Hunter**, Iş ortağı Direktörü Program Yöneticisi, .NET ekibi, Microsoft

> **Marta Füentes Lara**, Kabel

> **Raúl Fernández de kordobası**, Kabel

> **Antonio Manuel Fernández Cantos**, Kabel

## <a name="introduction"></a>Giriş

Bu kitapta, mevcut masaüstü uygulamalarınızı modernleştirme yolu aracılığıyla taşımak ve en son çalışma zamanı, dil ve platform özelliklerini birleştirmek için benimseyen stratejiler vardır. Her bir uygulama farklı olduğu için benzersiz tarif olmadığını ve bu nedenle gereksinimleriniz ve tercihleriniz olduğunu fark edeceksiniz. İyi haber, uygulamalarınıza yeni özellikler ve yetenekler eklemek için uygulayabileceğiniz yaygın yaklaşımlar vardır. Bunlar, kodunuzun önemli değişikliklere gerek kalmaz. Bu kitapta, tüm bu özelliklerin arka planda nasıl çalıştığını açığa çıkarıyoruz ve uygulamalarına ait olan mekanonları açıklayacağız. Üstelik, daha fazla şekilde gösterilen mevcut masaüstü uygulamalarını modernleştirmeye yönelik bazı yaygın senaryolar bulacaksınız. bu sayede, projelerinizi gelişmede daha fazla bilgi edinebilirsiniz.

Microsoft 'un mevcut uygulamaları modernleştirmeye yönelik yaklaşımı, kendi özelleştirilmiş yolunu oluşturma esnekliği vermektir. Bu kitapta açıklanan tüm modernleştirme stratejileri çoğunlukla bağımsızdır. Uygulamanız için uygun olanları seçebilir ve sizin için önemli olmayan diğerlerini atlayabilirsiniz. Diğer bir deyişle, uygulama gereksinimlerinizi en iyi şekilde karşılamak için stratejileri karıştırabilir ve eşleştirebilirsiniz.

## <a name="who-should-use-the-book"></a>Kitabı kimler kullanmalıdır?

.NET Core ve Windows 10 ' un avantajlarından yararlanmak için mevcut Windows Forms ve WPF masaüstü uygulamalarını modernleştirin isteyen geliştiriciler ve çözüm mimarları için bu kitabı yazdık.

Bu kitabı, kurumsal mimarde veya mevcut masaüstü uygulamalarını güncelleştirme avantajlarına genel bakış isteyen bir geliştirme lideri veya Direktörü gibi teknik bir karar veren bir yardım için de bulabilirsiniz.

## <a name="how-to-use-the-book"></a>Kitabı kullanma

Bu kitapta, "Neden", mevcut uygulamalarınızı nasıl modernleştirin isteyebileceğiniz ve NET Core 3,1 ve MSIX kullanarak masaüstü uygulamalarınızı modernleştirin 'e alacağınız belirli avantajlar ele alınmaktadır. Kitabın içeriği, genel bakış isteyen, ancak uygulama ve teknik, adım adım ayrıntılara odaklanmayı gerektirmeyen mimarlar ve teknik karar mekanizmaları için tasarlanmıştır.

Örnek uygulama kod parçacıkları ve ekran görüntüleri boyunca, örnek uygulamalar için tüm geçiş sürecini göstermek üzere Bölüm 5 ' le birlikte örnek uygulama kodu parçacıkları ve ekran görüntüleri sağlanır.

## <a name="what-this-book-doesnt-cover"></a>Bu kitabın kapsamıyor

Bu kitap, kaldırma ve kaydırma senaryolarına odaklanan belirli senaryolar alt kümesini kapsamakta ve kodu yeniden yazma çabalarına gerek kalmadan modernize almanın avantajlarından yararlanmanızı sağlar.

Bu kitapta, .NET Core ile modern uygulamalar geliştirilirken veya Windows Forms ve WPF ile çalışmaya başlama hakkında bilgi verilmez. Masaüstü geliştirme için en son teknolojilerle mevcut masaüstü uygulamalarını nasıl güncelleştirekullanabileceğinizi ele alınmaktadır.

## <a name="samples-used-in-this-book"></a>Bu kitapta kullanılan örnekler

Bir modernleştirmeyi gerçekleştirmek için gerekli adımları vurgulamak için adlı örnek bir uygulama kullanacağız `eShopModernizing` . Bu uygulamanın iki özelliği, Windows Forms ve WPF vardır ve her ikisinde de her ikisi de .NET Core 'a nasıl gerçekleştirileceği konusunda adım adım bir işlem göstereceğiz.

Ayrıca, bu kitabın GitHub deposunda, adım adım öğreticiyi izlemeye karar verirseniz, ile ilgili bir işlem sonuçları bulacaksınız.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kitap ve ilgili örnekler sürekli gelişiyor, bu nedenle geri bildiriminiz kullanıma açıldı! Bu kitabın nasıl iyileştirilen hakkında açıklamalara sahipseniz, [GitHub sorunları](https://github.com/dotnet/docs/issues)üzerinde oluşturulmuş herhangi bir sayfanın altındaki geri bildirim bölümünü kullanın.

>[!div class="step-by-step"]
>[Sonraki](why-modern-applications.md)
