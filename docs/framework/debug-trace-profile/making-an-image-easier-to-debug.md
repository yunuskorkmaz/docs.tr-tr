---
title: Görüntü .NET hata ayıklamayı kolaylaştırma
description: Anahtarları IDE kullanarak daha kolay hata ayıklama için yürütülebilir bir imaj yapılandırmak ve komut satırı seçenekleri öğrenin.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f25eaaa17d4c4bd2e9522591bb0fd66445cdb6f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541668"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>Görüntü .NET hata ayıklamayı kolaylaştırma

Yönetilmeyen kod derlenirken ayar IDE anahtarlar veya komut satırı seçenekleri tarafından hata ayıklama için yürütülebilir bir imaj yapılandırabilirsiniz. Örneğin, kullanabileceğiniz /**zı** Visual c++ komut satırı seçeneği hata ayıklama sembol dosyalarını (dosya uzantısı .pdb) yaymak için isteyebilir. Benzer şekilde, /**Od** iyileştirme devre dışı bırakmak için derleyici komut satırı seçeneği bildirir. Elde edilen kod daha yavaş çalışır, ancak bu gerekli olmalıdır hata ayıklamak daha kolay olur.

.NET Framework derleme yönetilen kod, Visual C++, Visual Basic ve C# gibi derleyicileri, kaynak programın Microsoft Ara diline (MSIL) derleyin. MSIL JIT olarak derlenmiş, yürütme, yerel makine koda hemen önce ise. Olarak yönetilmeyen kod ile ayar IDE anahtarlar veya komut satırı seçenekleri tarafından hata ayıklama için yürütülebilir bir imaj yapılandırabilirsiniz. Ayrıca, aynı şekilde çok hata ayıklama için JIT derleme yapılandırabilirsiniz.

JIT yapılandırmanın iki boyutu vardır:

- İzleme bilgileri JIT Derleyici isteyebilir. Bu, hata ayıklayıcı için MSIL oluşan bir zincir makine kodu karşılığı ile eşleşecek şekilde ve yerel değişkenlere ve işlev bağımsız değişkenleri depolandığı izlemenizi mümkün kılar. İstekte gerekmez. Bu nedenle .NET Framework sürüm 2.0 ile başlayarak, JIT Derleyici her zaman izleme bilgilerini oluşturur.

- Sonuçta elde edilen makine kodu şekilde JIT derleyicisi isteyebilir.

Normalde, oluşturduğu MSIL derleyici bu JIT Derleyici seçeneklerinin gerektiği gibi IDE anahtarlar veya örneğin, belirttiğiniz komut satırı seçenekleri göre ayarlar /**Od**.

Bazı durumlarda, böylece makine ürettiği kodu hata ayıklama daha kolaydır, JIT Derleyici davranışını değiştirmek isteyebilirsiniz. Örneğin, izleme bilgileri bir perakende derleme için JIT oluşturmak veya en iyi duruma getirme denetlemek isteyebilirsiniz. Bir başlatma (.ini) dosyası ile bunu yapabilirsiniz.

Örneğin, derleme, hata ayıklamak istiyorsanız adlı *MyApp.exe*, adlı bir metin dosyasını oluşturup *MyApp.ini*, aynı klasörde *MyApp.exe*, içeren Bu üç satırı:

```txt
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Her seçeneğin değeri 0 veya 1 olarak ayarlayabilirsiniz ve herhangi bir mevcut seçeneği 0 olarak varsayılır. Ayarı `GenerateTrackingInfo` 1 ve `AllowOptimize` kolay hata ayıklama 0 olarak sağlar.

.NET Framework sürüm 2.0 ile başlayarak, JIT Derleyici her zaman değerinden bağımsız izleme bilgilerini oluşturur `GenerateTrackingInfo`; ancak `AllowOptimize` değeri yine de bir etkiye sahiptir. Kullanırken [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) iyileştirme olmadan yerel görüntü derleneceği .ini dosya hedef klasörde mevcut olmalıdır `AllowOptimize=0` zaman Ngen.exe yürütür. Bir derlemeyi iyileştirme olmadan önceden derlenmiş, NGen.exe kullanarak önceden derlenmiş kodu kaldırmanız gerekir **/ uninstall** gibi en iyi duruma getirilmiş kodu önceden derlemek için Ngen.exe yeniden çalıştırmadan önce seçeneği. .İni dosyası klasörde mevcut değilse, varsayılan olarak Ngen.exe kodu en iyi duruma getirilmiş olarak işlemini gerçekleştirir.

<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> Derleme ayarlarını denetler. **DebuggableAttribute** JIT derleyicisi ve/veya en iyi duruma getirme izleme bilgileri oluşturan olup olmadığını denetleyen iki alan içerir. .NET Framework sürüm 2.0 ile başlayarak, JIT Derleyici her zaman bir izleme bilgilerini oluşturur.

Bir perakende derleme için derleyiciler herhangi ayarlamamanız **DebuggableAttribute**. Varsayılan olarak, JIT Derleyici en yüksek performans, makine kodu hata ayıklama uygulamalarınızdaki oluşturur. JIT izleme biraz performansı düşürür, etkinleştirip devre dışı bırakma iyileştirme çok performansı düşürür.

**DebuggableAttribute** aynı anda tüm bir derleme, derleme içindeki tek tek modülleri için geçerlidir. Geliştirme araçları gerekir bu nedenle ekleme özel öznitelikler için bütünleştirilmiş kod meta veri belirteci, bir derleme zaten oluşturuldu, veya sınıfa çağrılır, **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. ALink Aracı'nı sonra bunlar yükseltir **DebuggableAttribute** her modül öznitelikleri derlemeye bunlar bir bir parçası haline gelir. Bir çakışma varsa, ALINK işlemi başarısız olur.

> [!NOTE]
> Microsoft Visual C++ derleyicisi sürümünde .NET Framework 1.0 ekler **DebuggableAttribute** olduğunda **/CLR** ve **/zi** derleyici seçenekleri belirtilir. Sürümünde .NET Framework 1.1, veya eklemelisiniz **DebugabbleAttribute** el ile kod veya kullanım, **assemblydebug** bağlayıcı seçeneği.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama, İzleme ve Profil Oluşturma](../../../docs/framework/debug-trace-profile/index.md)
- [JIT-Ekleme Hata Ayıklamayı Etkinleştirme](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)
- [Profil oluşturmayı etkinleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
