---
title: "İstemci tarafı doğrulama (sunu katmanlarında doğrulama)"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | İstemci tarafı doğrulama (sunu katmanlarında doğrulama)"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: db88a3b5c95afdc8d5a20094105f1f5991483ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>İstemci tarafı doğrulama (sunu katmanlarında doğrulama)

Gerçekte kaynak etki alanı modeldir ve sonuç olarak etki alanı model düzeyinde doğrulama olmalıdır bile hem etki alanı model düzeyinde (sunucu tarafı) hem de istemci tarafında doğrulama hala işlenebilir.

İstemci tarafı doğrulama kullanıcıların harika bir kolaylık sağlamaya yöneliktir. Gidiş dönüş bekleniyor aksi harcadığınız zamanı doğrulama hataları döndürebilir sunucuya kaydeder. İş açısından, saniyede yüzlerce kez her gün çarpılan bile birkaç kesirlerini ekler miktarda zaman, gider ve aksiliklerin. Basit ve hemen doğrulama daha verimli olarak çalışabilir ve giriş ve çıkış daha iyi kalite üretmek kullanıcıların sağlar.

Yalnızca görünüm modeli ve etki alanı modeli farklı olduğundan, görünüm model doğrulama ve etki alanı model doğrulama benzer ancak farklı bir amaca hizmet eder. Endişe ediyorsanız bu durumda kodu yeniden kullanma bağlantı da gelebilir ve kurumsal uygulamalarda sunucu tarafı KURU ilkesini izleyin üzere daha istemci tarafı için eşleştiği değil daha da önemlisi KURU (yok yineleyin kendiniz İlkesi) hakkında göz önünde bulundurun.

Bile istemci tarafı doğrulama kullanırken, her zaman komutlarınızı doğrulamak veya gerekir sunucunun API'leri olası bir saldırı vektörü olduğundan sunucu kodunda DTOs giriş. Genellikle, her ikisini de yapmak UX açısından, bir istemci uygulaması varsa öngörülü ve geçersiz bilgi girmek için kullanıcıya izin verme en iyi olduğu için en iyi sonucu olur.

Bu nedenle, istemci-tarafı kodu, genellikle ViewModels doğrulayın. İstemci doğrulama hizmetlere göndermeden önce DTOs veya komutları çıktı.

İstemci tarafı doğrulama uyarlamasını ne tür bir istemci uygulaması oluşturmakta olduğunuz bağlıdır. .NET, JavaScript veya TypeScript, kodlanmış bu doğrulama SPA web uygulamasıyla kodda çoğunu MVC web uygulaması Web verilerle doğrulama gerekirse farklı olacak veya mobil uygulama, Xamarin ve C ile kodlanmış\#.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="validation-in-xamarin-mobile-apps"></a>Xamarin mobil uygulamalarda doğrulama

-   **Metin giriş ve hataları göster doğrulamak**
    [*https://developer.xamarin.com/recipes/ios/standard\_denetimleri/metin\_alan ve doğrulama\_giriş /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **Doğrulama geri çağırma**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>ASP.NET Core uygulamaları doğrulama

-   **Rick Anderson. Doğrulama ekleme**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>SPA doğrulama Web uygulamaları (Açısal 2, TypeScript, JavaScript)

-   **ADO Kukic. Açısal 2 Form doğrulama** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **Form doğrulama**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **Doğrulama.** Kolay belgeleri.
    [*http://BREEZE.github.io/doc-js/Validation.HTML*](http://breeze.github.io/doc-js/validation.html)

Özet olarak, doğrulama gelince en önemli kavramları şunlardır:

-   Varlıklar ve toplamalar kendi tutarlılığı zorlamak ve gerekir "her zaman geçerli". Birleşik kökleri aynı toplama içinde varlıkla tutarlılık sorumludur.

-   Bir varlık geçersiz bir durum girin olması gerektiğini düşünüyorsanız, farklı nesne modelini kullanarak göz önünde bulundurun — Örneğin, son etki alanı varlığı oluşturana kadar geçici DTO kullanma.

-   Bir toplama gibi birkaç ilişkili nesneleri oluşturmanız gerekir ve bunların tümünün oluşturulduktan sonra yalnızca geçerli olduğu, Fabrika düzeni kullanmayı düşünün.

-   Bir altyapı Framework'te güçlü bir bağımlılık uygulamanız gerekir çünkü doğrulama çerçeveleri sunu katmanı veya uygulama/hizmet katmanı gibi belirli katmanlarında ancak genellikle etki alanı modeli katmanı, en iyi şekilde kullanılır.

-   Uygulama proaktif olabileceği için istemci tarafı yedekli doğrulama sahip iyi durumlarda çoğunda istenir.


>[!div class="step-by-step"]
[Önceki] (etki alanı-model-katman-validations.md) [sonraki] (etki alanı-olayları-design-implementation.md)
