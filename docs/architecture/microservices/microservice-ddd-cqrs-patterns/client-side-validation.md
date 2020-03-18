---
title: İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | İstemci tarafı doğrulamanın temel kavramlarını keşfedin.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295997"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>İstemci tarafı doğrulaması (sunum katmanlarında doğrulama)

Gerçeğin kaynağı etki alanı modeli olsa ve sonuçta etki alanı modeli düzeyinde doğrulama olması gerekir, doğrulama hala etki alanı modeli düzeyinde (sunucu tarafı) ve UI (istemci tarafı) hem de işlenebilir.

İstemci tarafı doğrulama kullanıcılar için büyük bir kolaylıktır. Aksi takdirde doğrulama hataları döndürebilir sunucuya bir gidiş dönüş için bekleyen harcamak zaman kazandırır. İş açısından, saniyebile birkaç kesirleri her gün yüzlerce kez çarpılır zaman, gider ve hayal kırıklığı bir sürü ekler. Basit ve anında doğrulama, kullanıcıların daha verimli çalışmasını ve daha kaliteli giriş ve çıktı üretmesini sağlar.

Görünüm modeli ve etki alanı modeli farklı olduğu gibi, görünüm modeli doğrulama ve etki alanı modeli doğrulama benzer olabilir ama farklı bir amaca hizmet. DRY (Kendini TekrarEtme ilkesi) konusunda endişeleriniz varsa, bu durumda kodun yeniden kullanılmasının bağlantı anlamına gelebileceğini ve kurumsal uygulamalarda sunucu tarafını istemci tarafına çiftle etmemenin DRY ilkesine uymaktan daha önemli olduğunu düşünün.

İstemci tarafı doğrulamayı kullanırken bile, sunucu API'leri olası bir saldırı vektörü olduğundan, komutlarınızı her zaman doğrulamanız veya sunucu kodundaki DTO'lar girin. Genellikle, her ikisini de yapmak en iyi bahistir, çünkü ux perspektifinden bir istemci uygulamanız varsa, proaktif olmak ve kullanıcının geçersiz bilgileri girmesine izin vermemek en iyisidir.

Bu nedenle, istemci tarafı kodunda genellikle Görünüm Modelleri doğrular. Ayrıca, istemci çıktı DTOs veya komutları hizmetlere göndermeden önce doğrulayabilir.

İstemci tarafı doğrulamanın uygulanması, ne tür istemci uygulaması oluşturmakta olduğunuza bağlıdır. Bir web MVC web uygulamasındaki verileri .NET'teki kodun çoğuyla, JavaScript veya TypeScript'te kodlanmış bir SPA web uygulamasına veya Xamarin ve C# kodlu bir mobil uygulamayla doğruluyorsanız, bu farklı olacaktır.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="validation-in-xamarin-mobile-apps"></a>Xamarin mobil uygulamalarında doğrulama

- **Metin Girişini Doğrula ve Hataları Göster** \
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- **Doğrulama Geri Arama** \
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a>ASP.NET Core uygulamalarında doğrulama

- **Rick Anderson' ı. Doğrulama ekleme** \
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>SPA Web uygulamalarında doğrulama (Açısal 2, TypeScript, JavaScript)

- **Ado Kukiç. Açısal 2 Form Doğrulama** \
  <https://scotch.io/tutorials/angular-2-form-validation>

- **Form Doğrulama** \
  <https://angular.io/guide/form-validation>

- **Doğrulama.** Meltem belgeleri. \
  <https://breeze.github.io/doc-js/validation.html>

Özetle, doğrulama ile ilgili en önemli kavramlar şunlardır:

- Varlıklar ve agregalar kendi tutarlılıklarını uygulamalı ve "her zaman geçerli" olmalıdır. Toplam kökler, aynı toplam içinde çoklu varlık tutarlılığından sorumludur.

- Bir varlığın geçersiz bir durum girmesi gerektiğini düşünüyorsanız, örneğin, son etki alanı varlığını oluşturana kadar geçici bir DTO kullanarak farklı bir nesne modeli kullanmayı düşünün.

- Bir agrega gibi birkaç ilgili nesne oluşturmanız gerekiyorsa ve bunların yalnızca tümü oluşturulduktan sonra geçerliyse, Fabrika deseni kullanmayı düşünün.

- Çoğu durumda, uygulama proaktif olabileceğinden, istemci tarafında gereksiz doğrulama olması iyidir.

>[!div class="step-by-step"]
>[Önceki](domain-model-layer-validations.md)
>[Sonraki](domain-events-design-implementation.md)
