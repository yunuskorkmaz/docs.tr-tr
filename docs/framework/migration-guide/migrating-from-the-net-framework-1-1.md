---
title: .NET Framework 1.1'den Geçiş
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: f74b75827770524299f9a25a5854503186139cb4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126290"
---
# <a name="migrating-from-the-net-framework-11"></a>.NET Framework 1.1'den Geçiş

Windows işletim sisteminin [!INCLUDE[win7](../../../includes/win7-md.md)] ve sonraki sürümleri, .NET Framework 1,1 desteklemez. Sonuç olarak, .NET Framework 1,1 ' i hedefleyen uygulamalar [!INCLUDE[win7](../../../includes/win7-md.md)] veya sonraki işletim sistemi sürümlerinde hiçbir değişiklik yapılmadan çalışmaz. Bu konuda, Windows işletim sisteminin [!INCLUDE[win7](../../../includes/win7-md.md)] ve sonraki sürümlerinde 1,1 .NET Framework hedefleyen bir uygulamayı çalıştırmak için gereken adımlar ele alınmaktadır. .NET Framework 1,1 ve [!INCLUDE[win8](../../../includes/win8-md.md)]hakkında daha fazla bilgi için bkz. [Windows 8 ve sonraki sürümlerde .NET Framework 1,1 uygulamaları çalıştırma](../install/run-net-framework-1-1-apps.md).

## <a name="retargeting-or-recompiling"></a>Yeniden hedefleme veya yeniden derleme

[!INCLUDE[win7](../../../includes/win7-md.md)] veya sonraki bir Windows işletim sisteminde çalıştırmak için 1,1 .NET Framework kullanılarak derlenen bir uygulamayı almanın iki yolu vardır:

- .NET Framework 4 ve sonraki sürümlerde çalıştırmak için uygulamayı yeniden hedefleyebilirsiniz. Yeniden hedefleme, uygulamanın yapılandırma dosyasına .NET Framework 4 ve sonraki sürümlerde çalışmasına izin veren bir [\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) öğesi eklemenizi gerektirir. Bu tür bir yapılandırma dosyası aşağıdaki biçimi alır:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- .NET Framework 4 veya sonraki bir sürümünü hedefleyen bir derleyici ile uygulamayı yeniden derleyebilirsiniz. Çözümünüzü geliştirmek ve derlemek için ilk olarak Visual Studio 2003 kullandıysanız, çözümü Visual Studio 2010 ' de (ve belki de sonraki sürümlerde) açabilir ve **Proje uyumluluğu** iletişim kutusunu kullanarak çözümü ve proje dosyalarını Visual Studio 2003 tarafından Microsoft Build Engine (MSBuild) biçiminde kullanılan biçimler.

Uygulamanızı yeniden derlemeyi veya yeniden hedeflemeniz tercih etmeksizin, uygulamanızın .NET Framework sonraki sürümlerinde tanıtılan değişikliklerden etkilenip etkilenmediğini belirlemeniz gerekir. Bu değişiklikler iki tür:

- .NET Framework .NET Framework 1,1 ve sonraki sürümleri arasında gerçekleşen son değişiklikler.

- .NET Framework 1,1 ve sonraki .NET Framework sürümleri arasında kullanım dışı veya kullanımdan kaldırılmış olarak işaretlenmiş türler ve tür üyeleri.

Uygulamanızı yeniden hedeflemenize veya yeniden derlemenize bakılmaksızın, .NET Framework 1,1 ' den sonra yayınlanan .NET Framework her sürümü için hem son değişiklikleri hem de eski türleri ve üyeleri gözden geçirmeniz gerekir.

## <a name="breaking-changes"></a>Yeni Değişiklikler

Son değişiklik gerçekleştiğinde, belirli değişikliğe bağlı olarak, yeniden hedeflenen ve yeniden derlenen uygulamalar için geçici bir çözüm bulunabilir. Bazı durumlarda, önceki davranışı geri yüklemek için uygulamanızın yapılandırma dosyasının [\<çalışma zamanı >](../configure-apps/file-schema/startup/supportedruntime-element.md) öğesine bir alt öğe ekleyebilirsiniz. Örneğin, aşağıdaki yapılandırma dosyası .NET Framework 1,1 ' de kullanılan dize sıralamayı ve karşılaştırma davranışını geri yükler ve yeniden hedeflenmiş ya da yeniden derlenmiş bir uygulama ile kullanılabilir.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Ancak, bazı durumlarda, kaynak kodunuzu değiştirmeniz ve uygulamanızı yeniden derlemeniz gerekebilir.

Uygulamanızdaki olası son değişikliklerin etkisini değerlendirmek için aşağıdaki değişiklik listelerini gözden geçirmeniz gerekir:

- [.NET Framework 2,0 ' deki önemli değişiklikler](https://go.microsoft.com/fwlink/?LinkId=125263) , .NET Framework 1,1 ' i hedefleyen bir uygulamayı etkileyebilecek .NET Framework 2,0 SP1 'deki değişiklikleri belgelemektedir.

- [.NET Framework 3,5 SP1 'Deki değişiklikler](https://go.microsoft.com/fwlink/?LinkID=186989) , .NET Framework 3,5 ve .NET Framework 3,5 SP1 arasındaki değişiklikleri belgelemektedir.

- [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md) .NET Framework 3,5 SP1 ile .NET Framework 4 arasındaki değişiklikleri belgeler.

## <a name="obsolete-types-and-members"></a>Eski türler ve Üyeler

Kullanım dışı bırakılan türlerin ve üyelerin etkileri, yeniden hedeflenecek uygulamalar ve uygulamaları yeniden derlenmesi için biraz farklıdır. Eski tür veya üye derlemeden fiziksel olarak kaldırılmadığı takdirde, artık kullanılmayan türlerin ve üyelerin kullanılması yeniden hedeflenen uygulamayı etkilemez. Eski türleri veya üyeleri kullanan bir uygulamayı yeniden derleme, genellikle derleyici hatası yerine bir derleyici uyarısı üretir. Ancak, bazı durumlarda bir derleyici hatası oluşturur ve eski türü veya üyeyi kullanan kod başarıyla derlenmez. Bu durumda, uygulamanızı yeniden derlemeniz için önce eski türü veya üyeyi çağıran kaynak kodu yeniden yazmanız gerekir. Eski türler ve Üyeler hakkında daha fazla bilgi için bkz. [Sınıf kitaplığındaki artık kullanılmıyor](../whats-new/whats-obsolete.md).

.NET Framework 2,0 SP1 'in yayımlanmasından bu yana kullanımdan kaldırılan türlerin ve üyelerin etkisini değerlendirmek için bkz. [Sınıf kitaplığındaki yenilikler nelerdir](../whats-new/whats-obsolete.md). .NET Framework 2,0 SP1, 3,5 .NET Framework ve .NET Framework 4 için eski türlerin ve üyenin listesini gözden geçirin.
