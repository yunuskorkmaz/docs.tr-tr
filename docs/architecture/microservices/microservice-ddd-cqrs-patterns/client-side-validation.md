---
title: İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | İstemci tarafı doğrulamanın temel kavramlarını gezin.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295997"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)

Gerçeği kaynağı etki alanı modeli olduğu ve sonunda etki alanı model düzeyinde doğrulamanız gerektiğinde bile, doğrulama yine de etki alanı modeli düzeyinde (sunucu tarafında) ve Kullanıcı arabiriminde (istemci tarafında) işlenebilir.

İstemci tarafı doğrulama, kullanıcılar için harika bir kolaylık. Aksi takdirde, doğrulama hataları döndürebilecek sunucuya gidiş dönüş için bekleyen harcamaları zaman kazandırır. İş koşullarında, birkaç saniyelik bir saniyede yüzlerce kez, her gün çok fazla zaman, harcama ve hapasyon ekler. Basit ve anında doğrulama, kullanıcıların daha verimli bir şekilde çalışmasını sağlar ve daha iyi kalitede giriş ve çıktı üretebilir.

Görüntüleme modeli ve etki alanı modelinin farklı olduğu gibi, model doğrulamasını görüntüleyin ve etki alanı modeli doğrulaması da benzer olabilir, ancak farklı bir amaç sunabilir. KURUTMA (Kendini Tekrarlama prensibi) konusunda endişeleriniz varsa, bu durumda kodu yeniden kullanım için de bir de bu şekilde, kurumsal uygulamalarda sunucu tarafında kuru prensibi takip etmekle aynı şekilde sunucu tarafında daha önemli olduğunu düşünün.

İstemci tarafı doğrulaması kullanılırken bile, sunucu API 'Leri olası bir saldırı vektörü olduğundan, komutlarınızı veya sunucu kodundaki DTOs girdisini her zaman doğrulamalısınız. Genellikle, bir UX perspektifinden bir istemci uygulamanız varsa, bu, en iyi uygulamadır ve kullanıcının geçersiz bilgiler girmesine izin vermez.

Bu nedenle, istemci tarafı kodunda genellikle Viewmodellerini doğrularsınız. Ayrıca, Hizmetleri hizmetlere göndermeden önce istemci çıktı DTOs veya komutlarını da doğrulayabilirsiniz.

İstemci tarafı doğrulama uygulaması, oluşturmakta olduğunuz istemci uygulaması türüne bağlıdır. Bir Web MVC web uygulamasındaki verileri .NET 'teki kodun çoğuna, JavaScript veya TypeScript 'te kodlandığı bir SPA Web uygulamasına ya da Xamarin ve C#ile kodlanmış bir mobil uygulamaya doğruladıysanız bu, farklı olacaktır.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="validation-in-xamarin-mobile-apps"></a>Xamarin mobil uygulamalarında doğrulama

- **Metin girişi doğrulama ve hataları gösterme** \
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- **Doğrulama geri çağırma** \
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a>ASP.NET Core uygulamalarda doğrulama

- **Rick Anderson. Doğrulama \ ekleniyor**
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>SPA Web uygulamalarında doğrulama (angular 2, TypeScript, JavaScript)

- **ADO KuKic. Angular 2 formu doğrulama** \
  <https://scotch.io/tutorials/angular-2-form-validation>

- **Form doğrulama** \
  <https://angular.io/guide/form-validation>

- **Doğrulamasına.** Belgeleri yeniden Başlat. \
  <https://breeze.github.io/doc-js/validation.html>

Özet bölümünde, doğrulama için en önemli kavramlar şunlardır:

- Varlıklar ve toplamalar kendi tutarlılığını zorunlu tutar ve "her zaman geçerli" olmalıdır. Toplam kökler, aynı toplama içindeki çok varlıklık tutarlılığından sorumludur.

- Bir varlığın geçersiz bir durum girmesi gerektiğini düşünüyorsanız, farklı bir nesne modeli kullanmayı düşünün — Örneğin, son etki alanı varlığını oluşturana kadar geçici bir DTO kullanma.

- Toplama gibi çeşitli ilgili nesneler oluşturmanız gerekiyorsa ve bunlar yalnızca tümü oluşturulduktan sonra geçerliyse, fabrika modelini kullanmayı düşünün.

- Çoğu durumda, istemci tarafında gereksiz doğrulama yapmak iyi bir uygulamadır çünkü uygulama öngörülü olabilir.

>[!div class="step-by-step"]
>[Önceki](domain-model-layer-validations.md)
>[İleri](domain-events-design-implementation.md)
