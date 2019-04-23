---
title: .NET Framework'te sürüm uyumluluğu
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dda2cf99bdd3152e234bec4a143a7ab5ebd4cae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977021"
---
# <a name="version-compatibility-in-the-net-framework"></a>.NET Framework'te sürüm uyumluluğu

Geriye dönük uyumluluk, bir platformun belirli bir sürümü için geliştirilen bir uygulamanın o platformun sonraki sürümlerinde çalışır anlamına gelir. .NET Framework, geriye dönük uyumluluğu en üst düzeye çıkarmaya çalışır: .NET Framework'ün sonraki sürümlerinde .NET Framework sürümü için yazılan kaynak kodu derlemeniz gerekir ve .NET Framework'ün sonraki sürümlerinde .NET Framework sürümünde çalışan ikili dosyaları aynı şekilde davranır.

## <a name="Apps"></a> Uygulamalar için sürüm uyumluluğu

Varsayılan olarak, bir uygulama derlendiği .NET Framework sürümünde çalışır. Bu sürümü mevcut değilse ve uygulama yapılandırma dosyası desteklenen sürümleri tanımlamaz, bir .NET Framework başlatma hatası oluşabilir. Bu durumda, uygulamayı çalıştırma denemesi başarısız olur.

Uygulamanızın üzerinde çalıştığı belirli sürümler tanımlamak için bir veya daha fazla Ekle [ \<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) uygulamanızın yapılandırma dosyasına öğeleri. Her `<supportedRuntime>` öğesi çalışma zamanı ile ilk desteklenen bir sürümünü listeler en çok tercih edilen sürümü ve son sırada en az tercih edilen sürümü belirten.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Daha fazla bilgi için [nasıl yapılır: Bir uygulamayı destek .NET Framework 4 veya 4.x yapılandırma](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Bileşenler için sürüm uyumluluğu

Uygulama, onu çalışır, ancak bir bileşen bunu yapamaz .NET Framework sürümünü denetleyebilir. Bileşenler ve sınıf kitaplıkları belirli bir uygulama bağlamında yüklenir ve İşte bu nedenle zaman otomatik olarak uygulamanın çalıştığı .NET Framework sürümünde çalışır.

Bu kısıtlama nedeniyle, uyumluluk garantileri bileşenler için özellikle büyük/küçük harf önemlidir. .NET Framework 4 ile başlayarak, bir bileşene uygulayarak birden çok sürüm genelinde uyumlu kalmasını bekleme derecesini belirtebilirsiniz <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> bileşenin özniteliği. Araçlar, uyumluluk olası ihlallerini bir bileşenin gelecek garanti algılamak için bu özniteliği kullanabilirsiniz.

## <a name="backward-compatibility-and-the-net-framework"></a>Geriye dönük uyumluluk ve .NET Framework

Geriye dönük olarak uyumlu .NET Framework 4.5 ve sonraki sürümlerinde .NET Framework'ün önceki sürümleriyle oluşturulmuş uygulamalar. Diğer bir deyişle, uygulamaları ve bileşenleri önceki sürümlerle derlenmiş değişiklik yapılmadan .NET Framework 4.5 ve sonraki sürümlerinde çalışır. Ancak, varsayılan olarak, uygulamanızın .NET Framework 4.5 veya sonraki sürümler üzerinde çalışmasını etkinleştirmek için bir yapılandırma dosyası sağlamanız gerekebilir. Bu nedenle, bunlar geliştirilen, ortak dil çalışma zamanı sürümünde uygulamalar çalıştırın. Daha fazla bilgi için [uygulamalar için sürüm uyumluluğu](#Apps) bu makalenin önceki kısımlarında bölümü.

Uygulamada bu uyumluluk .NET Framework ve programlama tekniklerindeki görünüşte değişimlerle bölünebilir. Örneğin, .NET Framework 4.5 performans geliştirmeleri, önceki sürümlerinde gerçekleşmeyen bir yarış durumu açığa çıkarabilir. Benzer şekilde, .NET Framework derlemelerine yönelik sabit kodlanmış bir yol kullanarak, belirli bir .NET Framework sürümü ile denklik karşılaştırması gerçekleştirme ve yansıma kullanarak bir özel alanın değerinin alınması geriye dönük olarak uyumlu uygulamalar değildir. Ayrıca, .NET Framework'ün her sürümü, hata düzeltmeleri ve bazı uygulamaların ve bileşenlerin uyumluluğunu etkileyebilecek güvenlikle ilgili değişiklikler içerir.

Uygulama veya bileşen .NET Framework 4.5 (.NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8 onun nokta sürümleri dahil) üzerinde beklenen şekilde çalışmazsa, aşağıdaki denetim listelerini kullanın:

-  Uygulamanızı geliştirilmiştir, .NET Framework 4.0 ile başlayan .NET Framework'ün herhangi bir sürümünü çalıştırmak için bkz: [.NET Framework'te uygulama uyumluluğu](application-compatibility.md) hedeflenen .NET Framework sürümünüz arasında değişiklik listesini oluşturmak için ve uygulamanızın üzerinde çalıştığı sürümü.

- Bir .NET Framework 3.5 uygulamanız varsa, ayrıca bkz: [.NET Framework 4 geçiş sorunları](../migration-guide/net-framework-4-migration-issues.md).

- Bir .NET Framework 2.0 uygulamanız varsa, ayrıca bkz: [.NET Framework 3.5 SP1 içindeki değişiklikleri](https://go.microsoft.com/fwlink/?LinkId=186989).

- Bir .NET Framework 1.1 uygulamanız varsa, ayrıca bkz: [.NET Framework 2.0 içindeki değişiklikleri](https://go.microsoft.com/fwlink/?LinkID=125263).

- .NET Framework 4.5 veya onun nokta sürümleri çalıştırmak için mevcut kaynak kodu yeniden derlemeden ya da bir uygulama veya bileşen .NET Framework 4.5 hedefleyen yeni bir sürümünü, geliştirmekte olduğunuz ya da mevcut bir kaynak kod temel nokta sürümlerini, denetleyin[Sınıf Kitaplığı'nda ne kullanılmıyor](../whats-new/whats-obsolete.md) için eski türler ve üyeler ve açıklanan geçici çözümü uygulayın. (Önceden derlenmiş kod türleri ve üyeleri artık kullanılmıyor olarak işaretlenmiş karşı çalışmaya devam eder.)

- .NET Framework 4.5 değişikliği uygulamanızı bozduğunu belirlerseniz, kontrol [çalışma zamanı Ayarları Şeması](../configure-apps/file-schema/runtime/index.md)ve özellikle [ \<AppContextSwitchOverrides > öğesi](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), bir çalışma zamanı ayarı uygulamanızın yapılandırma dosyasında önceki davranışı geri yüklemek için kullanabileceğiniz olup olmadığını belirler.

- Soruna arasında belgelenmemiştir geliyorsa, bir sorun açın [.NET Geliştirici topluluğu sitesini](https://developercommunity.visualstudio.com/spaces/61/index.html) veya bir sorun açın [Microsoft/dotnet GitHub deposunu](https://github.com/microsoft/dotnet/issues).

## <a name="compatibility-and-side-by-side-execution"></a>Uyumluluk ve yan yana yürütme

Yönelik uygun geçici bir çözüm bulamazsanız, .NET Framework 4.5 (veya onun nokta sürümleri biri) 1.1, 2.0 ve 3.5 sürümleri ile yan yana çalışır ve sürüm 4 yerini alan bir yerinde güncelleştirme olduğunu unutmayın. 1.1, 2.0 ve 3.5 sürümlerini hedefleyen uygulamalar için uygulamayı en iyi ortamında çalıştırmak amacıyla hedef makineye .NET Framework'ün uygun sürümünü yükleyebilirsiniz. Yan yana yürütme hakkında daha fazla bilgi için bkz. [yan yana yürütme](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yenilikler](../whats-new/index.md)
- [Sınıf Kitaplığında Artık Kullanılmayanlar](../whats-new/whats-obsolete.md)
- [Uygulama Uyumluluğu](../migration-guide/application-compatibility.md)
- [Microsoft .NET Framework Destek Ömrü İlkesi](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [.NET framework 4 geçiş sorunları](../migration-guide/net-framework-4-migration-issues.md)
