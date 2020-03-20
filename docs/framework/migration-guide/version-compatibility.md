---
title: .NET Framework'de sürüm uyumluluğu
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: e0de18b5a40875d1fec2633c16688111d8f4b9ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73974949"
---
# <a name="version-compatibility-in-the-net-framework"></a>.NET Framework'de sürüm uyumluluğu

Geriye dönük uyumluluk, bir platformun belirli bir sürümü için geliştirilen bir uygulamanın bu platformun sonraki sürümlerinde çalışacağı anlamına gelir. .NET Framework geriye dönük uyumluluğu en üst düzeye çıkarmaya çalışır: .NET Framework'ün bir sürümü için yazılan kaynak kodu .NET Framework'ün sonraki sürümlerinde derlenmelidir ve .NET Framework'ün bir sürümünde çalışan ikili ler aynı şekilde .NET Framework'ün sonraki sürümleri.

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a>Uygulamalar için sürüm uyumluluğu

Varsayılan olarak, bir uygulama .NET Framework'ün için inşa edildiği sürümünde çalışır. Bu sürüm yoksa ve uygulama yapılandırma dosyası desteklenen sürümleri tanımlamıyorsa, .NET Framework başlatma hatası oluşabilir. Bu durumda, uygulamayı çalıştırma girişimi başarısız olur.

Uygulamanızın çalıştığı belirli sürümleri tanımlamak için, uygulamanızın yapılandırma dosyasına bir veya daha fazla [ \<desteklenen Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) öğesi ekleyin. Her `<supportedRuntime>` öğe, ilk en çok tercih edilen sürümü ve en son en az tercih edilen sürümü belirten ile çalışma zamanıdesteklenen bir sürümünü listeler.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Daha fazla bilgi için [bkz: Bir Uygulamayı Destekleyecek şekilde yapılandırın .NET Framework 4 veya 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Bileşenler için sürüm uyumluluğu

Bir uygulama çalıştığı .NET Framework sürümünü denetleyebilir, ancak bileşen denetemez. Bileşenler ve sınıf kitaplıkları belirli bir uygulama bağlamında yüklenir ve bu nedenle uygulamanın çalıştığı .NET Framework sürümünde otomatik olarak çalıştırılırlar.

Bu kısıtlama nedeniyle, uyumluluk garantileri özellikle bileşenler için önemlidir. .NET Framework 4'ten başlayarak, bu bileşene özniteliği uygulayarak bir bileşenin <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> birden çok sürümde uyumlu kalmasının beklendiği dereceyi belirtebilirsiniz. Araçlar bu özelliği, bir bileşenin gelecekteki sürümlerinde uyumluluk garantisinin olası ihlallerini algılamak için kullanabilir.

## <a name="backward-compatibility-and-the-net-framework"></a>Geriye dönük uyumluluk ve .NET Çerçevesi

.NET Framework 4.5 ve sonraki sürümler,.NET Framework'ün önceki sürümleriyle oluşturulmuş uygulamalarla geriye dönük uyumludur. Başka bir deyişle, önceki sürümlerle oluşturulmuş uygulamalar ve bileşenler .NET Framework 4.5 ve sonraki sürümlerde değişiklik yapılmadan çalışır. Ancak, varsayılan olarak, uygulamalar geliştirildiği ortak dil çalışma zamanı sürümünde çalışır, bu nedenle uygulamanızın .NET Framework 4.5 veya sonraki sürümlerinde çalışmasını sağlamak için bir yapılandırma dosyası sağlamanız gerekebilir. Daha fazla bilgi için, bu makalenin başlarında uygulamalar için [Sürüm uyumluluğu](#Apps) bölümüne bakın.

Uygulamada, bu uyumluluk .NET Framework'deki önemsiz gibi görünen değişiklikler ve programlama tekniklerinde yapılan değişikliklerle bozulabilir. Örneğin, .NET Framework 4.5'teki performans iyileştirmeleri, önceki sürümlerde oluşmayan bir yarış koşulunu ortaya çıkarabilir. Benzer şekilde, .NET Framework derlemelerine sabit kodlanmış bir yol kullanmak, .NET Framework'ün belirli bir sürümüyle eşitlik karşılaştırması yapmak ve yansımayı kullanarak özel bir alanın değerini almak geriye doğru uyumlu uygulamalar değildir. Buna ek olarak, .NET Framework'ün her sürümü, hata düzeltmeleri ve bazı uygulamaların ve bileşenlerin uyumluluğunu etkileyebilecek güvenlikle ilgili değişiklikleri içerir.

Uygulamanız veya bileşeniniz .NET Framework 4.5'te beklendiği gibi çalışmıyorsa (puan sürümleri dahil,.NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8) aşağıdaki denetim listelerini kullanın:

- Uygulamanız .NET Framework 4.0 ile başlayan .NET Framework'ün herhangi bir sürümünde çalışacak şekilde geliştirilmişse, hedeflenenene .NET Framework sürümü ile uygulamanızın yayınlandığı sürüm arasında değişikliklerin listesini oluşturmak için [Uygulama uyumluluğuna](application-compatibility.md) bakın.

- Bir .NET Framework 3.5 uygulamanız varsa, [.NET Framework 4 Geçiş Sorunları'na](../migration-guide/net-framework-4-migration-issues.md)da bakın.

- Bir .NET Framework 2.0 uygulamanız varsa, [.NET Framework 3.5 SP1'deki değişikliklere](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10))de bakın.

- Bir .NET Framework 1.1 uygulamanız varsa, [.NET Framework 2.0'daki değişikliklere](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10))de bakın.

- .NET Framework 4.5 veya nokta sürümlerinde çalışacak şekilde varolan kaynak kodunu yeniden derlİyorsanız veya .NET Framework 4.5'i hedefleyen bir uygulama veya bileşenin yeni bir sürümünü veya varolan bir kaynak kodu tabanından nokta sürümlerini geliştiriyorsanız, [Sınıf Kitaplığı'nda](../whats-new/whats-obsolete.md) eski türleri ve üyeleri için Nelerin Eskidiğini kontrol edin ve açıklanan geçici çözüme uygulayın. (Daha önce derlenmiş kod, eski olarak işaretlenmiş türlere ve üyelere karşı çalışmaya devam edecektir.)

- .NET Framework 4.5'teki bir değişikliğin uygulamanızı bozarak kırdığını belirlerseniz, önceki davranışı geri yüklemek için uygulamanızın yapılandırma dosyasında çalışma zamanı ayarını kullanıp kullanamayacağınızı belirlemek için [Çalışma Zamanı Ayarları Şemasını](../configure-apps/file-schema/runtime/index.md)ve özellikle [ \<AppContextSwitchOverrides> Öğesi'ni](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)kontrol edin.

- Belgelenmemiş bir sorunla karşılaşırsanız, [.NET için Geliştirici Topluluğu sitesinde](https://developercommunity.visualstudio.com/spaces/61/index.html) bir sorun açın veya [Microsoft/dotnet GitHub repo'sunda](https://github.com/microsoft/dotnet/issues)bir sorun açın.

## <a name="compatibility-and-side-by-side-execution"></a>Uyumluluk ve yan yana yürütme

Sorununuzun için uygun bir geçici çözüm bulamıyorsanız, .NET Framework 4.5'in (veya puan açıklamalarından biri) 1.1, 2.0 ve 3.5 sürümleriyle yan yana çalıştığını ve sürüm 4'ün yerini alan yerinde bir güncelleştirme olduğunu unutmayın. 1.1, 2.0 ve 3.5 sürümlerini hedefleyen uygulamalar için, uygulamayı en iyi ortamda çalıştırmak için .NET Framework'ün uygun sürümünü hedef makineye yükleyebilirsiniz. Yan yana yürütme hakkında daha fazla bilgi için, [Yan yana Yürütme'ye](../deployment/side-by-side-execution.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yenilikler](../whats-new/index.md)
- [Sınıf Kitaplığı'nda Artık Kullanılmayanlar](../whats-new/whats-obsolete.md)
- [Uygulama Uyumluluğu](../migration-guide/application-compatibility.md)
- [.NET Framework resmi destek politikası](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 Geçiş Sorunları](../migration-guide/net-framework-4-migration-issues.md)
