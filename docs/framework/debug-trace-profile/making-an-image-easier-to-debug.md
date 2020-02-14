---
title: .NET sürümünde bir görüntünün hata ayıklamayı kolaylaştırın
description: IDE anahtarlarını ve komut satırı seçeneklerini kullanarak daha kolay hata ayıklama için yürütülebilir bir görüntünün nasıl yapılandırılacağını öğrenin.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
ms.openlocfilehash: 44d512a8ebec0e21e33f51c07428331e5e22b7bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217335"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>.NET sürümünde bir görüntünün hata ayıklamayı kolaylaştırın

Yönetilmeyen kod derlenirken, IDE anahtarlarını veya komut satırı seçeneklerini ayarlayarak hata ayıklama için çalıştırılabilir bir görüntü yapılandırabilirsiniz. Örneğin, hata ayıklama sembol dosyalarını (dosya uzantısı. pdb) yaymasını Istemek C++ Için Visual 'teki/zı komut satırı seçeneğini kullanabilirsiniz. Benzer şekilde,/**od** komut satırı seçeneği derleyiciye iyileştirmeyi devre dışı bırakmayı söyler. Elde edilen kod daha yavaş çalışır, ancak bunun daha kolay hata ayıklaması gerekir, bu gerekli olacaktır.

.NET Framework yönetilen kodu derlerken, görsel C++gibi derleyiciler, Visual Basic ve C# kaynak programını MICROSOFT ara dili (MSIL) olarak derler. MSIL daha sonra, yürütmeden önce, yerel makine koduna, daha sonra JıT olarak derlenir. Yönetilmeyen kodda olduğu gibi, IDE anahtarlarını veya komut satırı seçeneklerini ayarlayarak hata ayıklama için çalıştırılabilir bir görüntü yapılandırabilirsiniz. Ayrıca, JıT derlemesini hata ayıklama için aynı şekilde de yapılandırabilirsiniz.

Bu JıT yapılandırmasının iki yönü vardır:

- İzleme bilgilerini oluşturmak için JıT derleyicisini isteyebilirsiniz. Bu, hata ayıklayıcının makine kodu karşılık gelen bir MSIL zinciri ile eşleşmesini ve yerel değişkenlerin ve işlev bağımsız değişkenlerinin nerede depolandığını izlemenizi olanaklı kılar. .NET Framework sürüm 2,0 ' den başlayarak, JıT derleyicisi her zaman izleme bilgilerini oluşturur, bu nedenle isteği isteme gereksinimi yoktur.

- Elde edilen makine kodunu iyileştirmeden JıT derleyicisini isteyebilirsiniz.

Normalde, MSIL 'yi üreten derleyici bu JıT derleyici seçeneklerini, belirttiğiniz IDE anahtarlarına veya komut satırı seçeneklerine göre (örneğin,/**od**) uygun şekilde ayarlar.

Bazı durumlarda, JıT derleyicisinin davranışını, oluşturduğu makine kodunun hata ayıklaması daha kolay olacak şekilde değiştirmek isteyebilirsiniz. Örneğin, bir perakende derleme veya denetim iyileştirmesi için JıT izleme bilgileri oluşturmak isteyebilirsiniz. Bunu bir başlatma (. ini) dosyası ile yapabilirsiniz.

Örneğin, hata ayıklamak istediğiniz derleme *MyApp. exe*olarak adlandırılmışsa, MyApp. *ini*adlı bir metin dosyasını aşağıdaki üç satırı içeren *MyApp. exe*ile aynı klasörde oluşturabilirsiniz:

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Her seçeneğin değerini 0 veya 1 olarak ayarlayabilir ve yok seçeneğinin varsayılan değeri 0 ' dır. `GenerateTrackingInfo` 1 ' e ve `AllowOptimize` 0 ' a ayarlamak en kolay hata ayıklamayı sağlar.

.NET Framework sürüm 2,0 ' den başlayarak, JıT derleyicisi `GenerateTrackingInfo`değerinden bağımsız olarak her zaman izleme bilgilerini oluşturur; Ancak, `AllowOptimize` değeri hala bir etkiye sahiptir. [Ngen. exe ' yi (yerel görüntü Oluşturucu)](../tools/ngen-exe-native-image-generator.md) kullanırken, yerel görüntüyü iyileştirme olmadan önceden derlemek Için, Ngen. exe yürütüldüğünde. ini dosyası hedef klasörde bulunmalıdır `AllowOptimize=0`. En iyi duruma getirme olmadan bir derlemeyi önceden derlenmiş hale getirdiniz, Ngen. exe ' yi yeniden çalıştırmadan önce Ngen **. exe '** yi kullanarak önceden derlenmiş kodu kaldırmalısınız. . İni dosyası klasöründe yoksa, varsayılan olarak Ngen. exe kodu en iyileştirilmiş olarak önceden derler.

<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType>, bir derlemenin ayarlarını denetler. Hata ayıklama **Ggableattribute** , JIT derleyicisinin izleme bilgilerini iyileştirip/veya üretmeyeceğini denetleyen iki alan içerir. .NET Framework sürüm 2,0 ' den başlayarak, JıT derleyicisi her zaman izleme bilgilerini oluşturur.

Bir perakende derlemesi için, derleyiciler herhangi bir hata ayıklama **Ggableattribute**ayarlanmamış. Varsayılan olarak, JIT derleyicisi makine kodunda hata ayıklamak için en yüksek performansı, en zor 'yi oluşturur. JıT izlemenin etkinleştirilmesi performansı biraz düşürür ve en iyi duruma getirme performansı çok büyük ölçüde azaltır.

Hata ayıklama **Ggableattribute** , derleme içindeki ayrı modüller için değil, bir kerede tüm derleme için geçerlidir. Bu nedenle geliştirme araçları, derleme meta veri belirtecine, bir derleme zaten oluşturulmuşsa veya **System. Runtime. CompilerServices. AssemblyAttributesGoHere**adlı sınıfa özel öznitelikler iliştirmelidir. Sonra ALink aracı **, bu hata** ayıklama kodu özniteliklerini her modülden bir parçası haline geldikleri derlemeye yükseltir. Bir çakışma varsa, ALink işlemi başarısız olur.

> [!NOTE]
> .NET Framework sürüm 1,0 ' de C++ , **/clr** ve **/Zi** derleyici seçenekleri belirtildiğinde Microsoft Visual derleyicisi, hata **ayıklayıcıggableattribute** öğesini ekler. .NET Framework sürüm 1,1 ' de, hata **ayıklıbağlantı özniteliği** kodunuza el ile eklemeniz veya **/ASSEMBLYDEBUG** bağlayıcı seçeneğini kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama, İzleme ve Profil Oluşturma](index.md)
- [JIT-Ekleme Hata Ayıklamayı Etkinleştirme](enabling-jit-attach-debugging.md)
- [Profil oluşturmayı etkinleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
