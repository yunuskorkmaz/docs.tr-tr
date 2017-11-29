---
title: "Görüntüde Hata Ayıklamayı Kolaylaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 46a9c11f3545e5d2b9f91572a87ee2614810e4d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="making-an-image-easier-to-debug"></a>Görüntüde Hata Ayıklamayı Kolaylaştırma
Yönetilmeyen kod derlerken ayar IDE anahtarları veya komut satırı seçenekleri tarafından hata ayıklama için yürütülebilir görüntü yapılandırabilirsiniz. Örneğin, kullanabileceğiniz /**Zi** Visual c++ komut satırı seçeneği, hata ayıklama simge dosyaları (dosya uzantısı .pdb) yaymak üzere isteyebilir. Benzer şekilde, /**Od** iyileştirme devre dışı bırakmak için derleyici komut satırı seçeneği söyler. Ortaya çıkan kodu daha yavaş çalışır, ancak bu gerekli olmalıdır hata ayıklamak daha kolay olur.  
  
 .NET Framework derleme yönetilen kodu, Visual C++, Visual Basic ve C# gibi derleyicileri kendi kaynak program Microsoft Ara dili (MSIL içine) derler. MSIL sonradan JIT-derlenmiş, yerel makine koda yürütme hemen önce. Olarak yönetilmeyen kod ile ayar IDE anahtarları veya komut satırı seçenekleri tarafından hata ayıklama için yürütülebilir görüntü yapılandırabilirsiniz. Ayrıca, benzer şekilde hata ayıklama için JIT derleme yapılandırabilirsiniz.  
  
 Bu JIT yapılandırma iki boyutu vardır:  
  
-   İzleme bilgileri oluşturmak için JIT Derleyici isteyebilir. Hata ayıklayıcı için MSIL zincirinde makine kodu karşılığı ile eşleşen ve yerel değişkenleri ve işlev bağımsız değişkenleri depolandığı izlemek için mümkün kılar.  .NET Framework sürüm 2. 0'da, bu yüzden istekte gerek JIT Derleyici izleme bilgilerini her zaman oluşturur.  
  
-   Sonuçta elde edilen makine kodu iyileştirmeyecek şekilde JIT Derleyici isteyebilir.  
  
 Normalde, MSIL oluşturur derleyici bu JIT Derleyici Seçenekleri uygun şekilde, IDE anahtarları veya belirttiğiniz, örneğin, komut satırı seçenekleri göre ayarlar /**Od**.  
  
 Bazı durumlarda, böylece hata ayıklamak makine ürettiği kodu kolaydır JIT Derleyici davranışını değiştirmek isteyebilirsiniz. Örneğin, JIT izleme perakende derleme bilgilerini oluşturmak veya en iyi duruma getirme denetlemek isteyebilirsiniz. Bir başlatma (.ini) dosyası bunu yapabilirsiniz.  
  
 Örneğin, MyApp.exe hata ayıklamak istediğiniz derleme çağrılırsa, bu üç satırları içeriyorsa MyApp.exe ile aynı klasörde MyApp.ini adlı bir metin dosyası oluşturabilirsiniz:  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 Herhangi bir etmeksizin seçeneği 0 olarak varsayılan olarak ve her seçeneğin değeri, 0 veya 1'e ayarlayabilirsiniz. Ayarı `GenerateTrackingInfo` 1 ve `AllowOptimize` kolay hata ayıklama 0 olarak sağlar.  
  
> [!NOTE]
>  .NET Framework sürüm 2. 0'da, JIT Derleyici her zaman izleme bilgilerini değerinden bağımsız oluşturur `GenerateTrackingInfo`; ancak, `AllowOptimize` değeri hala bir etkisi vardır. Kullanırken [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) en iyi duruma getirme olmadan yerel görüntü derleneceği .ini dosyası ile hedef klasördeki mevcut olmalıdır `AllowOptimize=0` zaman Ngen.exe yürütür. En iyi duruma getirme olmayan bir derleme önceden derlenmiş NGen.exe kullanarak önceden derlenmiş kod kaldırmanız gerekir **/ uninstall** en iyi duruma getirilmiş gibi kodu önceden derlemek için Ngen.exe yeniden çalıştırmadan önce seçeneği. .İni dosyası klasörde mevcut değilse, varsayılan olarak Ngen.exe kodu en iyi duruma getirilmiş gibi işlemini gerçekleştirir.  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> Derleme ayarlarını denetler. **DebuggableAttribute** olup JIT Derleyici en iyi duruma getirme ve/veya izleme bilgileri oluşturmak için kayıt ayarları iki alanları içerir. .NET Framework sürüm 2. 0'da, JIT Derleyici her zaman izleme bilgilerini oluşturur.  
  
> [!NOTE]
>  Bir perakende derleme için herhangi bir derleyicileri ayarlamayın **DebuggableAttribute**. JIT Derleyici varsayılan davranışı, yüksek performans, makine kodda hata ayıklama en zor oluşturmaktır. JIT etkinleştirme biraz izleme performansı düşürür ve devre dışı bırakma iyileştirme çok performansı düşürür.  
  
> [!NOTE]
>  **DebuggableAttribute** aynı anda tüm bir derleme değil, tek tek modülleri bütünleştirilmiş kod içinde uygulanır. Geliştirme araçları bu nedenle eklemeniz gerekir özel öznitelikler derlemesi meta veri simgesi için bir derleme zaten oluşturulduğundan, veya sınıfına adlı varsa **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. ALink aracı sonra bunlar yükseltmez **DebuggableAttribute** derleme her modül öznitelikleriyle olduklarında bir parçası. Bir çakışma varsa, ALink işlemi başarısız olur.  
  
> [!NOTE]
>  Microsoft Visual C++ Derleyici sürümünde .NET Framework 1.0 ekler **DebuggableAttribute** zaman **/CLR** ve **/zı** derleyici seçenekleri belirtilir. Sürümünde .NET Framework 1.1, ya da eklemelisiniz **DebugabbleAttribute** el ile kod veya kullanım içinde **/ASSEMBLYDEBUG** bağlayıcı seçeneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama, izleme ve profil oluşturma](../../../docs/framework/debug-trace-profile/index.md)  
 [JIT-ekleme hata ayıklama etkinleştirme](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 [Profil oluşturma etkinleştirme](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)
