---
title: Roslyn Çözümleyicileri - .NET tabanlı.
description: Sorunları bulmak ve bu sorunlara yönelik düzeltmeler önerir tabanlı Roslyn Çözümleyicileri hakkında bilgi edinin.
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.technology: dotnet-standard
---

# <a name="the-roslyn-based-analyzers"></a>Roslyn Çözümleyicilerini tabanlı

Roslyn tabanlı Çözümleyicileri, sorunları bulup düzeltme Öner projenizin kaynak kodunu analiz etmek için .NET derleyici SDK'sı (Roslyn API'leri) kullanın. Farklı Çözümleyicileri sorunları, güvenlik konuları API'sini uyumluluk hataları neden olabilecek uygulamalar arasında değişen farklı sınıflardaki arayın.

Roslyn tabanlı Çözümleyicileri, etkileşimli ve yapılar sırasında hem de çalışır. Çözümleyici, Visual Studio'da veya komut satırı derlemeleri farklı konusunda rehberlik yapmaktadır.

Visual Studio'da kod düzenleme yaparken kaygıları tetikleyen kod oluşturma hemen sonra olası sorunları yakalama değişiklik yaptıkça Çözümleyicileri çalıştırın. Herhangi bir sorun, herhangi bir sorun altında dalgalı çizgiler ile vurgulanmıştır. Visual Studio bir ampul görüntüler ve üzerine tıkladığınızda Çözümleyicisi Bu sorun için olası düzeltmeler önerir. Proje oluşturduğunuzda, Visual Studio veya komut satırından, tüm kaynak kodunu analiz edilir ve Çözümleyicisi olası sorunların tam bir listesini sağlar. Aşağıdaki şekilde, bir örnek gösterilmektedir.

![framework Çözümleyicisi tarafından bildirilen sorunları](./media/framework-analyzers-2.png)

Roslyn tabanlı Çözümleyicileri hataları, uyarıları ve sorunun önem derecesine göre bilgi olarak olası sorunları bildirir.

Roslyn tabanlı Çözümleyicileri NuGet paketleri olarak projenize yükleyin. Yapılandırılmış Çözümleyicileri ve her Çözümleyicisi ayarları geri ve bu proje için tüm geliştirici makinesinde çalıştırın.

> [!NOTE]
> Roslyn tabanlı Çözümleyicileri için kullanıcı deneyimi, kod analiz kitaplıklarını FxCop ve güvenlik analizi araçları daha eski sürümleri gibi çok farklıdır.  Roslyn tabanlı Çözümleyicileri açıkça çalıştırmanız gerekmez. Visual Studio'da "Çözümle" menüsünde "Kod analizini Çalıştır" menü öğelerini kullanmasına gerek yoktur. Roslyn tabanlı Çözümleyicileri, siz çalıştığınız sırada zaman uyumsuz olarak çalışır.

## <a name="more-information-on-specific-analyzers"></a>Özel çözümleyiciler hakkında daha fazla bilgi

Bu bölümde aşağıdaki Çözümleyicileri ele alınmaktadır:

* [API Çözümleyicisi](api-analyzer.md): Bu çözümleyici inceler, kodunuz için olası uyumluluk riskleri veya kullanımdan kaldırılan API'leri kullanır.
* [Framework Çözümleyicisi](framework-analyzer.md): Bu Çözümleyici, .NET Framework uygulamaları için yönergelerine uyduğundan emin olmak için kodunuzu inceler. Bu kurallar, çeşitli güvenlik tabanlı önerileri içerir.
* [.NET portability Analyzer](portability-analyzer.md): Bu çözümleyici ne kadar iş uygulamanızın diğer .NET uygulamaları ve .NET Core, .NET standart, UWP ve Xamarin iOS, Android ve Mac için dahil olmak üzere ile uyumlu hale getirmek için gerekli olduğunu görmek için kodunuzu inceler.
