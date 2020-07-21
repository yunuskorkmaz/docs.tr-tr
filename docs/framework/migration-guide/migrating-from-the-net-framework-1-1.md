---
title: .NET Framework 1.1'den Geçiş
description: Windows 7 veya sonraki sürümlerde .NET Framework 1,1 kullanılarak derlenen bir uygulamayı çalıştırmak için gereken adımlar hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: f2b0e21ff5dbeab3395335f52799629859fb2d90
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475274"
---
# <a name="migrate-from-the-net-framework-11"></a>.NET Framework 1,1 ' den geçirin

Windows 7 ve sonraki Windows işletim sistemi sürümleri 1,1 .NET Framework desteklemez. Sonuç olarak, .NET Framework 1,1 ' i hedefleyen uygulamalar, Windows 7 veya sonraki işletim sistemi sürümlerinde hiçbir değişiklik yapılmadan çalıştırılmayacak. Bu konuda, Windows 7 ve sonraki Windows işletim sistemi sürümlerinde 1,1 .NET Framework hedefleyen bir uygulamayı çalıştırmak için gereken adımlar ele alınmaktadır. 1,1 ve Windows 8 .NET Framework hakkında daha fazla bilgi için bkz. [Windows 8 ve sonraki sürümlerde .NET Framework 1,1 uygulamaları çalıştırma](../install/run-net-framework-1-1-apps.md).

## <a name="retarget-or-recompile"></a>Yeniden hedefle veya yeniden derleme

Windows 7 veya sonraki bir Windows işletim sisteminde çalıştırmak için 1,1 .NET Framework kullanılarak derlenen bir uygulamayı almanın iki yolu vardır:

- .NET Framework 4 ve sonraki sürümlerde çalıştırmak için uygulamayı yeniden hedefleyin. Yeniden hedefleme [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) , uygulamanın yapılandırma dosyasına .NET Framework 4 ve sonraki sürümlerde çalışmasına izin veren bir öğe eklemenizi gerektirir. Bu tür bir yapılandırma dosyası aşağıdaki biçimi alır:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- .NET Framework 4 veya sonraki bir sürümünü hedefleyen bir derleyici ile uygulamayı yeniden derleyin. Çözümünüzü geliştirmek ve derlemek için ilk olarak Visual Studio 2003 kullandıysanız, çözümü Visual Studio 2010 ' de açabilir (ve belki de sonraki sürümlerde) ve **Proje uyumluluğu** iletişim kutusunu kullanarak çözümü ve proje dosyalarını visual Studio 2003 tarafından kullanılan biçimlerden Microsoft Build Engine (MSBuild) biçimine dönüştürebilirsiniz.

Uygulamanızı yeniden derlemeyi veya yeniden hedeflemeniz tercih etmeksizin, uygulamanızın .NET Framework sonraki sürümlerinde tanıtılan değişikliklerden etkilenip etkilenmediğini belirlemeniz gerekir. Bu değişiklikler iki tür:

- .NET Framework .NET Framework 1,1 ve sonraki sürümleri arasında gerçekleşen son değişiklikler.

- .NET Framework 1,1 ve sonraki .NET Framework sürümleri arasında kullanım dışı veya kullanımdan kaldırılmış olarak işaretlenmiş türler ve tür üyeleri.

Uygulamanızı yeniden hedeflemenize veya yeniden derlemenize bakılmaksızın, .NET Framework 1,1 ' den sonra yayınlanan .NET Framework her sürümü için hem son değişiklikleri hem de eski türleri ve üyeleri gözden geçirmeniz gerekir.

## <a name="breaking-changes"></a>Yeni değişiklikler

Son değişiklik gerçekleştiğinde, belirli değişikliğe bağlı olarak, yeniden hedeflenen ve yeniden derlenen uygulamalar için geçici bir çözüm bulunabilir. Bazı durumlarda, [\<runtime>](../configure-apps/file-schema/startup/supportedruntime-element.md) önceki davranışı geri yüklemek için uygulamanızın yapılandırma dosyasının öğesine bir alt öğe ekleyebilirsiniz. Örneğin, aşağıdaki yapılandırma dosyası .NET Framework 1,1 ' de kullanılan dize sıralamayı ve karşılaştırma davranışını geri yükler ve yeniden hedeflenmiş ya da yeniden derlenmiş bir uygulama ile kullanılabilir.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Ancak, bazı durumlarda, kaynak kodunuzu değiştirmeniz ve uygulamanızı yeniden derlemeniz gerekebilir.

Uygulamanızdaki olası son değişikliklerin etkisini değerlendirmek için aşağıdaki değişiklik listelerini gözden geçirmeniz gerekir:

- [.NET Framework 2,0 ' deki önemli değişiklikler](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)) , .NET Framework 1,1 ' i hedefleyen bir uygulamayı etkileyebilecek .NET Framework 2,0 SP1 'deki değişiklikleri belgelemektedir.

- [.NET Framework 3,5 SP1 'Deki değişiklikler](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)) , .NET Framework 3,5 ve .NET Framework 3,5 SP1 arasındaki değişiklikleri belgelemektedir.

- [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md) .NET Framework 3,5 SP1 ile .NET Framework 4 arasındaki değişiklikleri belgeler.

## <a name="obsolete-types-and-members"></a>Eski türler ve Üyeler

Kullanım dışı bırakılan türlerin ve üyelerin etkileri, yeniden hedeflenecek uygulamalar ve uygulamaları yeniden derlenmesi için biraz farklıdır. Eski tür veya üye derlemeden fiziksel olarak kaldırılmadığı takdirde, artık kullanılmayan türlerin ve üyelerin kullanılması yeniden hedeflenen uygulamayı etkilemez. Eski türleri veya üyeleri kullanan bir uygulamayı yeniden derleme, genellikle derleyici hatası yerine bir derleyici uyarısı üretir. Ancak, bazı durumlarda bir derleyici hatası oluşturur ve eski türü veya üyeyi kullanan kod başarıyla derlenmez. Bu durumda, uygulamanızı yeniden derlemeniz için önce eski türü veya üyeyi çağıran kaynak kodu yeniden yazmanız gerekir. Eski türler ve Üyeler hakkında daha fazla bilgi için bkz. [Sınıf kitaplığındaki artık kullanılmıyor](../whats-new/whats-obsolete.md).

.NET Framework 2,0 SP1 'in yayımlanmasından bu yana kullanımdan kaldırılan türlerin ve üyelerin etkisini değerlendirmek için bkz. [Sınıf kitaplığındaki yenilikler nelerdir](../whats-new/whats-obsolete.md). .NET Framework 2,0 SP1, 3,5 .NET Framework ve .NET Framework 4 için eski türlerin ve üyenin listesini gözden geçirin.
