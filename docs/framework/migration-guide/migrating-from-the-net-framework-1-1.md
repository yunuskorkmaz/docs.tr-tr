---
title: .NET Framework 1.1'den Geçiş
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: 11fe9ba36d32a4c9fe363b48f76a8bb2b24f073b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73974964"
---
# <a name="migrate-from-the-net-framework-11"></a>.NET Framework 1.1'den geçirin

Windows işletim sisteminin Windows 7 ve sonraki sürümleri .NET Framework 1.1'i desteklemez. Sonuç olarak, .NET Framework 1.1'i hedefleyen uygulamalar Windows 7 veya daha sonraki işletim sistemi sürümlerinde değişiklik yapılmadan çalışmaz. Bu konu, Windows 7 ve Windows işletim sisteminin sonraki sürümleri altında .NET Framework 1.1 hedefleyen bir uygulamayı çalıştırmak için gereken adımları tartışır. .NET Framework 1.1 ve Windows 8 hakkında daha fazla bilgi için [Windows 8 ve sonraki sürümlerdeki Çalıştır .NET Framework 1.1 Uygulamalarını](../install/run-net-framework-1-1-apps.md)görün.

## <a name="retarget-or-recompile"></a>Yeniden hedefleme veya yeniden derleme

Windows 7 veya daha sonraki bir Windows işletim sisteminde çalıştırmak için .NET Framework 1.1 kullanılarak derlenen bir uygulamayı almanın iki yolu vardır:

- .NET Framework 4 ve sonraki sürümler altında çalışacak uygulamayı yeniden hedefle. Yeniden hedefleme, uygulamanın yapılandırma dosyasına .NET Framework 4 ve sonraki sürümler altında çalışmasını sağlayan desteklenen bir [ \<Runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) öğesi eklemenizi gerektirir. Böyle bir yapılandırma dosyası aşağıdaki formu alır:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Uygulamayı .NET Framework 4 veya daha sonraki bir sürümü hedefleyen bir derleyiciyle yeniden derle. Visual Studio 2003'ü çözümünüzü geliştirmek ve derlemek için kullandıysanız, çözümü Visual Studio 2010'da (ve muhtemelen sonraki sürümlerde) açabilir ve visual studio 2003 tarafından kullanılan biçimlerden çözüm ve proje dosyalarını Microsoft Build Engine (MSBuild) biçimine dönüştürmek için **Project Uyumluluk** iletişim kutusunu kullanabilirsiniz.

Uygulamanızı yeniden derlemeyi veya yeniden hedeflemeyi tercih edip etmediğinize bakılmaksızın, uygulamanızın .NET Framework'ün sonraki sürümlerinde yapılan değişikliklerden etkilenip etkilenmediğini belirlemeniz gerekir. Bu değişiklikler iki türdedir:

- .NET Framework 1.1 ve .NET Framework'ün sonraki sürümleri arasında meydana gelen sondakika değişiklikleri.

- .NET Framework 1.1 ve .NET Framework'ün sonraki sürümleri arasında amortismana alınmış veya eskimiş olarak işaretlenmiş tür ve tür üyeleri.

Uygulamanızı yeniden hedefleyin veya yeniden derleyin, .NET Framework 1.1'den sonra yayımlanan .NET Framework'ün her sürümü için hem son dakika değişikliklerini hem de eski türleri ve üyeleri gözden geçirmelisiniz.

## <a name="breaking-changes"></a>Yeni değişiklikler

Belirli bir değişikliğe bağlı olarak bir kesme değişikliği gerçekleştiğinde, yeniden hedeflenen ve yeniden derlenen uygulamalar için bir geçici çözüm kullanılabilir. Bazı durumlarda, önceki davranışı geri yüklemek [ \<](../configure-apps/file-schema/startup/supportedruntime-element.md) için uygulamanızın yapılandırma dosyasının çalışma süresi>öğesine bir alt öğe ekleyebilirsiniz. Örneğin, aşağıdaki yapılandırma dosyası .NET Framework 1.1'de kullanılan dize sıralama ve karşılaştırma davranışını geri yükler ve yeniden hedeflenen veya yeniden derlenmiş bir uygulamayla kullanılabilir.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Ancak, bazı durumlarda kaynak kodunuzu değiştirmeniz ve uygulamanızı yeniden derlemeniz gerekebilir.

Olası kırılma değişikliklerinin uygulamanız üzerindeki etkisini değerlendirmek için aşağıdaki değişiklik listelerini gözden geçirmeniz gerekir:

- [.NET Framework 2.0 belgelerinde .NET](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)) Framework 2.0 SP1'de .NET Framework 1.1'i hedefleyen bir uygulamayı etkileyebilecek değişiklikler.

- [.NET Framework 3.5 SP1 belgelerindeki değişiklikler](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)) .NET Framework 3.5 ve .NET Framework 3.5 SP1 arasındaki değişiklikler.

- [.NET Framework 4 Geçiş Sorunları](net-framework-4-migration-issues.md) belgeleri .NET Framework 3.5 SP1 ve .NET Framework 4 arasındaki değişiklikleri.

## <a name="obsolete-types-and-members"></a>Eski türleri ve üyeleri

Amortismana uymuş türlerin ve üyelerin etkisi, yeniden hedeflenen uygulamalar ve yeniden derlenen uygulamalar için biraz farklıdır. Eski türler ve üyelerin kullanımı, eski tür veya üye fiziksel olarak derlemesinden kaldırılmadığı sürece yeniden hedeflenen bir uygulamayı etkilemez. Eski türleri veya üyeleri kullanan bir uygulamayı yeniden derlemek genellikle derleyici hatası yerine derleyici uyarısı üretir. Ancak, bazı durumlarda, bir derleyici hatası üretir ve eski türü veya üyekullanan kod başarılı bir şekilde derlemez. Bu durumda, başvurunuzu yeniden derlemeden önce eski türü veya üyeyi çağıran kaynak kodunu yeniden yazmanız gerekir. Eski türler ve üyeler hakkında daha fazla bilgi için [Sınıf Kitaplığında Eski Ler](../whats-new/whats-obsolete.md)Nelerdir'e bakın.

.NET Framework 2.0 SP1'in yayımlanmasından bu yana amortismana ulaşmış türlerin ve üyelerin etkisini değerlendirmek için [Sınıf Kitaplığında Eski OlanA'ya](../whats-new/whats-obsolete.md)bakın. .NET Framework 2.0 SP1, .NET Framework 3.5 ve .NET Framework 4 için eski türler ve üye listelerini gözden geçirin.
