---
title: .NET sürümünde bir görüntünün hata ayıklamayı kolaylaştırın
description: IDE anahtarlarını ve komut satırı seçeneklerini kullanarak daha kolay hata ayıklama için yürütülebilir bir görüntünün nasıl yapılandırılacağını öğrenin.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
ms.openlocfilehash: a3305dc864e7852c2336009503732a51868410d2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558517"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>.NET sürümünde bir görüntünün hata ayıklamayı kolaylaştırın

Yönetilmeyen kod derlenirken, IDE anahtarlarını veya komut satırı seçeneklerini ayarlayarak hata ayıklama için çalıştırılabilir bir görüntü yapılandırabilirsiniz. Örneğin, hata ayıklama sembol dosyalarını (dosya uzantısı. pdb) yaymasını istemek için Visual C++ içindeki/**zı** komut satırı seçeneğini kullanabilirsiniz. Benzer şekilde,/**od** komut satırı seçeneği derleyiciye iyileştirmeyi devre dışı bırakmayı söyler. Elde edilen kod daha yavaş çalışır, ancak bunun daha kolay hata ayıklaması gerekir, bu gerekli olacaktır.

.NET Framework yönetilen kod derlenirken, Visual C++, Visual Basic ve C# gibi derleyiciler, kaynak programını Microsoft ara dili 'ne (MSIL) derler. MSIL daha sonra, yürütmeden önce, yerel makine koduna, daha sonra JıT olarak derlenir. Yönetilmeyen kodda olduğu gibi, IDE anahtarlarını veya komut satırı seçeneklerini ayarlayarak hata ayıklama için çalıştırılabilir bir görüntü yapılandırabilirsiniz. Ayrıca, JıT derlemesini hata ayıklama için aynı şekilde de yapılandırabilirsiniz.

Bu JıT yapılandırmasının iki yönü vardır:

- İzleme bilgilerini oluşturmak için JıT derleyicisini isteyebilirsiniz. Bu, hata ayıklayıcının makine kodu karşılık gelen bir MSIL zinciri ile eşleşmesini ve yerel değişkenlerin ve işlev bağımsız değişkenlerinin nerede depolandığını izlemenizi olanaklı kılar. .NET Framework sürüm 2,0 ' den başlayarak, JıT derleyicisi her zaman izleme bilgilerini oluşturur, bu nedenle isteği isteme gereksinimi yoktur.

- Elde edilen makine kodunu iyileştirmeden JıT derleyicisini isteyebilirsiniz.

Normalde, MSIL 'yi üreten derleyici bu JıT derleyici seçeneklerini, belirttiğiniz IDE anahtarlarına veya komut satırı seçeneklerine göre (örneğin,/**od**) uygun şekilde ayarlar.

Bazı durumlarda, JıT derleyicisinin davranışını, oluşturduğu makine kodunun hata ayıklaması daha kolay olacak şekilde değiştirmek isteyebilirsiniz. Örneğin, bir perakende derleme veya denetim iyileştirmesi için JıT izleme bilgileri oluşturmak isteyebilirsiniz. Bunu bir başlatma (. ini) dosyası ile yapabilirsiniz.

Örneğin, hata ayıklamak istediğiniz derleme *MyApp.exe*çağrılırsa, bu üç satırı içeren *MyApp.exe*aynı klasörde *MyApp.ini*adlı bir metin dosyası oluşturabilirsiniz:

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Her seçeneğin değerini 0 veya 1 olarak ayarlayabilir ve yok seçeneğinin varsayılan değeri 0 ' dır. `GenerateTrackingInfo`1 ve 0 olarak ayarlandığında `AllowOptimize` en kolay hata ayıklama sağlanır.

.NET Framework sürüm 2,0 ' den başlayarak, JıT derleyicisi her zaman için değerinden bağımsız olarak izleme bilgilerini oluşturur `GenerateTrackingInfo` ; ancak, `AllowOptimize` değer hala bir etkiye sahip olur. [Ngen.exe (yerel görüntü Oluşturucu)](../tools/ngen-exe-native-image-generator.md) kullanırken yerel görüntüyü iyileştirme olmadan önceden derlemek için, Ngen.exe yürütüldüğünde. ini dosyası hedef klasörde bulunmalıdır `AllowOptimize=0` . En iyi duruma getirme olmadan bir derlemeyi önceden derlenmiş yaparsanız, kodu en iyi duruma getirilmiş şekilde önceden derlemek için Ngen.exe yeniden çalıştırmadan önce önceden derlenmiş kodu NGen.exe **/Uninstall** seçeneğini kullanarak kaldırmanız gerekir. . İni dosyası klasörde yoksa, varsayılan olarak kodu en iyileştirilmiş olarak önceden derler Ngen.exe.

, <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> Bir derlemenin ayarlarını denetler. Hata ayıklama **Ggableattribute** , JIT derleyicisinin izleme bilgilerini iyileştirip/veya üretmeyeceğini denetleyen iki alan içerir. .NET Framework sürüm 2,0 ' den başlayarak, JıT derleyicisi her zaman izleme bilgilerini oluşturur.

Bir perakende derlemesi için, derleyiciler herhangi bir hata ayıklama **Ggableattribute**ayarlanmamış. Varsayılan olarak, JIT derleyicisi makine kodunda hata ayıklamak için en yüksek performansı, en zor 'yi oluşturur. JıT izlemenin etkinleştirilmesi performansı biraz düşürür ve en iyi duruma getirme performansı çok büyük ölçüde azaltır.

Hata ayıklama **Ggableattribute** , derleme içindeki ayrı modüller için değil, bir kerede tüm derleme için geçerlidir. Bu nedenle geliştirme araçları, derleme meta veri belirtecine, bir derleme zaten oluşturulmuşsa veya **System. Runtime. CompilerServices. AssemblyAttributesGoHere**adlı sınıfa özel öznitelikler iliştirmelidir. Sonra ALink aracı **, bu hata** ayıklama kodu özniteliklerini her modülden bir parçası haline geldikleri derlemeye yükseltir. Bir çakışma varsa, ALink işlemi başarısız olur.

> [!NOTE]
> .NET Framework sürüm 1,0 ' de, **/clr** ve **/Zi** derleyici seçenekleri belirtildiğinde Microsoft Visual C++ Derleyici, hata **ayıklayıcıggableattribute** öğesini ekler. .NET Framework sürüm 1,1 ' de, hata **ayıklıbağlantı özniteliği** kodunuza el ile eklemeniz veya **/ASSEMBLYDEBUG** bağlayıcı seçeneğini kullanmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama, Izleme ve profil oluşturma](index.md)
- [JIT-Ekleme Hata Ayıklamayı Etkinleştirme](enabling-jit-attach-debugging.md)
- [Profil oluşturmayı etkinleştirme](/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
