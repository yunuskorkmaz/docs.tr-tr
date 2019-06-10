---
title: .NET Framework 1.1'den Geçiş
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 441a65f9a72dd0fcffb062710df74bb529767cef
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816067"
---
# <a name="migrating-from-the-net-framework-11"></a>.NET Framework 1.1'den Geçiş

[!INCLUDE[win7](../../../includes/win7-md.md)] ve Windows işletim sisteminin sonraki sürümlerini .NET Framework 1.1 desteklemez. Sonuç olarak, .NET Framework 1.1 hedefleyen uygulamalar değişiklik olmadan çalışmaz [!INCLUDE[win7](../../../includes/win7-md.md)] veya sonraki bir işletim sistemi sürümleri. Bu konu altında .NET Framework 1.1 hedefleyen bir uygulamayı çalıştırmak için gerekli adımları ele alınmaktadır [!INCLUDE[win7](../../../includes/win7-md.md)] ve Windows işletim sisteminin sonraki sürümleri. .NET Framework 1.1 hakkında daha fazla bilgi ve [!INCLUDE[win8](../../../includes/win8-md.md)], bkz: [Windows 8 ve sonraki sürümlerinde .NET Framework 1.1 uygulamalarını çalıştırma](../../../docs/framework/install/run-net-framework-1-1-apps.md).

## <a name="retargeting-or-recompiling"></a>Yeniden hedefleme veya yeniden derleme

Çalıştırmak için .NET Framework 1.1 kullanılarak derlenen bir uygulamayı almanın iki yolu vardır [!INCLUDE[win7](../../../includes/win7-md.md)] veya sonraki bir Windows işletim sistemi:

- Uygulamayı .NET Framework 4 ve sonraki sürümler altında çalışacak şekilde hedefleyebilirsiniz. Yeniden hegefleme gerektiriyor eklediğiniz bir [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) .NET Framework 4 ve sonraki sürümler altında çalıştırılmasına izin verir uygulamanın yapılandırma dosyası öğesi. Bu tür bir yapılandırma dosyası, aşağıdaki biçimi alır:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Bir derleyici ile uygulamayı hedefleyen .NET Framework 4 veya sonraki bir sürümünü yeniden derleyebilirsiniz. İlk olarak geliştirme ve çözümünüzü derlemek için Visual Studio 2003 kullandıysanız, çözümü Visual Studio 2010'da açabilirsiniz (ve muhtemelen sonraki sürümlerinde çok) ve **proje uyumluluğu** çözüm dönüştürmek için iletişim kutusu ve Microsoft Build Engine (MSBuild) biçimine Visual Studio 2003'te kullanılan biçimlerden konumundan proje dosyaları.

Olup, yeniden derleyin veya uygulamanızı yeniden hedeflediğinizde tercih ettiğinize bakılmaksızın, uygulamanızın sonraki .NET Framework sürümlerinde sunulan değişikliklerden etkilenip etkilenmediğini belirlemeniz gerekir. Bu değişiklikler iki çeşittir:

- .NET Framework 1.1 ve sonraki sürümlerinde .NET Framework'ün arasında gerçekleşen değişikliklerin kesiliyor.

- Türleri ve kullanım dışı olarak işaretlenmiş veya sonraki sürümlerinde .NET Framework ve .NET Framework 1.1 arasında eski tür üyeleri.

Uygulamanızı yeniden hedeflediğinizde veya yeniden derlemeniz olsun, hem büyük değişiklikleri ve kullanılmayan türlerin ve üyelerin .NET Framework 1.1 sonra yayımlanmış olan .NET Framework'ün her sürümü için gözden geçirmelisiniz.

## <a name="breaking-changes"></a>Yeni Değişiklikler

Bir değişiklik gerçekleştiğinde, belirli değişikliğe bağlı olarak geçici bir çözüm kullanılabilir olan her ikisi için yeniden hedeflenmiş ve yeniden derlenmiş uygulamalar. Bazı durumlarda, bir alt öğesine ekleyebileceğiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) önceki davranışı geri yüklemek için uygulamanızın yapılandırma dosyasına öğesidir. Örneğin, dize sıralama şu yapılandırma dosyasını geri yükler ve karşılaştırma davranışını .NET Framework 1. 1 ' kullanılan ve bir yeniden hedeflenen ya da yeniden derlenmiş bir uygulama ile kullanılabilir.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Ancak, bazı durumlarda, kaynak kodunuzu değiştirmeniz ve uygulamanızı yeniden derlemeniz gerekebilir.

Uygulamanızdaki olası yeni değişikliklerin etkisini değerlendirmek için şu değişiklik listesini gözden geçirmeniz gerekir:

- [.NET Framework 2.0 sürümünde yeni değişiklikler](https://go.microsoft.com/fwlink/?LinkId=125263) .NET Framework 1.1 hedefleyen bir uygulamayı etkileyebilecek bir .NET Framework 2.0 SP1 içindeki belge değişiklikleri.

- [.NET Framework 3.5 SP1 içindeki değişiklikleri](https://go.microsoft.com/fwlink/?LinkID=186989) .NET Framework 3.5 arasındaki değişiklikleri belgeler ve [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)].

- [.NET framework 4 geçiş sorunları](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) arasındaki değişiklikleri belgeler [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] ve .NET Framework 4.

## <a name="obsolete-types-and-members"></a>Eski türler ve Üyeler

Kullanım dışı türlerin ve üyelerin etkisi, yeniden hedeflenen uygulamalar için biraz farklıdır ve yeniden derlenmiş uygulamalar. Eski türler ve üyeler kullanımını, eski türü veya üye fiziksel olarak derlemesinden kaldırılmadığı sürece yeniden hedeflenen uygulamayı etkilemez. Genellikle eski türleri veya üyeleri kullanan bir uygulama yeniden derlendiğinde, derleyici bir derleyici hatası yerine uyarısı üretilir. Ancak, bazı durumlarda, bir derleyici hatası oluşturur ve eski türü veya üyeyi kullanan kod başarıyla derleme yapmaz. Bu durumda, uygulamanızı yeniden derlemeden önce kullanılmayan tür veya üyeyi çağıran kaynak kodunu yeniden yazmanız gerekir. Eski türler ve üyeler hakkında daha fazla bilgi için bkz. [Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md).

Tür ve .NET Framework 2.0 SP1 sürümünden itibaren kullanımdan üyelerin etkisini değerlendirmek için bkz: [Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md). Eski tür ve üye listelerini gözden geçirmek için .NET Framework 2.0 SP1, .NET Framework 3.5 ve .NET Framework 4.
