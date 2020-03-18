---
title: Roslyn tabanlı Analizörler - .NET
description: Sorunları bulan ve bu sorunlar için düzeltmeler öneren Roslyn tabanlı çözümleyiciler hakkında bilgi edinin.
author: billwagner
ms.author: wiwagn
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 436cfb3904f0891f8c18bb5890563a13d65e2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "62003060"
---
# <a name="the-roslyn-based-analyzers"></a>Roslyn tabanlı Analizörler

Roslyn tabanlı çözümleyiciler, sorunları bulmak ve düzeltmeler önermek için projenizin kaynak kodunu çözümlemek için .NET Derleyici SDK'yı (Roslyn API'leri) kullanır. Farklı çözümleyiciler, hatalara neden olabilecek uygulamalardan güvenlik kaygılarına ve API uyumluluğuna kadar farklı sorun sınıfları arar.

Roslyn tabanlı çözümleyiciler hem etkileşimli hem de yapılar sırasında çalışır. Çözümleyici, Visual Studio'da veya komut satırında oluştururken farklı kılavuzlar sağlar.

Visual Studio'da kodu edinirken, siz değişiklikler yaptığınızda çözümleyiciler çalışır ve endişeleri tetikleyen kod oluşturur oluşturmaz olası sorunları yakalar. Herhangi bir sorun herhangi bir sorun altında squiggles ile vurgulanır. Visual Studio bir ampul görüntüler, ve üzerine tıkladığınızda analizör bu sorun için olası düzeltmeler önerecektir. Projeyi Visual Studio'da veya komut satırından oluşturduğunuzda, tüm kaynak kodu analiz edilir ve çözümleyici olası sorunların tam bir listesini sağlar. Aşağıdaki şekil bir örnek gösterir.

![çerçeve çözümleyicisi tarafından bildirilen sorunlar](./media/framework-analyzers-2.png)

Roslyn tabanlı çözümleyiciler, sorunun önem derecesine bağlı olarak olası sorunları hatalar, uyarılar veya bilgi olarak bildirir.

Projenizde Roslyn tabanlı çözümleyicileri NuGet paketleri olarak yüklersiniz. Yapılandırılan çözümleyiciler ve her çözümleyici için tüm ayarlar geri yüklenir ve bu proje için herhangi bir geliştiricinin makinesinde çalıştırılır.

> [!NOTE]
> Roslyn tabanlı analizörler için kullanıcı deneyimi FxCop eski sürümleri ve güvenlik analiz araçları gibi Kod Analizi kütüphaneleri farklıdır.  Roslyn tabanlı analizörleri açıkça çalıştırmanız gerekmez. Visual Studio'daki "Analiz Et" menüsündeki "Kod Analizini Çalıştır" menüsüöğelerini kullanmaya gerek yoktur. Roslyn tabanlı çözümleyiciler siz çalışırken eş zamanlı olarak çalışırlar.

## <a name="more-information-on-specific-analyzers"></a>Belirli analizörler hakkında daha fazla bilgi

Aşağıdaki çözümleyiciler bu bölümde ele alınmıştır:

* [API Çözümleyicisi](api-analyzer.md): Bu çözümleyici, olası uyumluluk riskleri veya amortismana alınan API'lerin kullanımı için kodunuzu inceler.
* [Çerçeve Çözümleyicisi](framework-analyzer.md): Bu çözümleyici, .NET Framework uygulamaları nın yönergelerine uyduğundan emin olmak için kodunuzu inceler. Bu kurallar, güvenlik tabanlı çeşitli öneriler içerir.
* [.NET Taşınabilirlik Çözümleyicisi](portability-analyzer.md): Bu çözümleyici, uygulamanızı iOS, Android ve Mac için .NET Core, .NET Standard, UWP ve Xamarin gibi diğer .NET uygulamaları ve profilleriyle uyumlu hale getirmek için ne kadar çalışma gerektiğini görmek için kodunuzu inceler.
