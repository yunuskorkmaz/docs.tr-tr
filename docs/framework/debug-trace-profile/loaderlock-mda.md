---
title: loaderLock MDA
description: .NET 'teki loaderLock yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin. Bu, yönetilen kodu Windows işletim sistemi yükleyicisi kilidini tutan bir iş parçacığında çalıştırma girişimlerini algılar.
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- LoaderLock MDA
- MDAs (managed debugging assistants), loader locks
- managed debugging assistants (MDAs), loader locks
- operating system loader locks
- loader locks
- locks, threads
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
ms.openlocfilehash: 055b07a805c5f0b613519d6019950a9b249a4b38
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051629"
---
# <a name="loaderlock-mda"></a>loaderLock MDA
`loaderLock`Yönetilen hata ayıklama Yardımcısı (MDA), Microsoft Windows işletim sistemi yükleyicisi kilidini tutan bir iş parçacığında yönetilen kodu yürütme girişimlerini algılar.  Bu tür bir yürütme kilitlenmeyle sonuçlanabileceğinden ve DLL 'lerin işletim sistemi yükleyicisi tarafından başlatılmadan önce kullanabilmesi nedeniyle geçersizdir.  
  
## <a name="symptoms"></a>Belirtiler  
 İşletim sisteminin yükleyici kilidi içinde kod yürütürken en yaygın hata, aynı zamanda yükleyici kilidi gerektiren diğer Win32 işlevlerini çağırmaya çalışırken iş parçacıklarının kilitlenmeleridir.  Bu işlevlere örnekler,, `LoadLibrary` `GetProcAddress` `FreeLibrary` ve `GetModuleHandle` .  Uygulama bu işlevleri doğrudan çağırmayabilir; ortak dil çalışma zamanı (CLR), daha üst düzey bir çağrının <xref:System.Reflection.Assembly.Load%2A> veya platform çağırma yöntemine yapılan ilk çağrının sonucu olarak bu işlevleri çağırabilir.  
  
 Kilitlenmeler Ayrıca bir iş parçacığının başlamasını veya bitmesini bekliyorsa meydana gelebilir.  Bir iş parçacığı başladığında veya yürütmeyi bitirdiğinde, etkilenen dll 'lere olay göndermek için işletim sisteminin yükleyici kilidini almalıdır.  
  
 Son olarak, dll 'lere yapılan çağrıların işletim sisteminin yükleyicisi tarafından düzgün bir şekilde başlatılmadan önce gerçekleşebileceği durumlar vardır.  Kilitlenmede yer alan tüm iş parçacıklarının yığınlarını inceleyerek tanılanabilir kilitlenme hatalarından farklı olarak, bu MDA ' ı kullanmadan başlatılmamış dll 'lerin kullanımını tanılamak çok zordur.  
  
## <a name="cause"></a>Nedeni  
 1,0 veya 1,1 .NET Framework sürümleri için oluşturulan karma yönetilen/yönetilmeyen C++ derlemeleri genellikle özel bir bakım yapılmadığı takdirde (örneğin, **/NOENTRY**ile bağlantı kurarak), yükleyici kilidi içinde yönetilen kodu yürütmeye çalışır.
  
 .NET Framework sürüm 2,0 için derlenmiş, karışık yönetilen/yönetilmeyen C++ derlemeleri bu sorunlara karşı daha düşüktür ve bu sorunlar, işletim sisteminin kurallarını ihlal eden yönetilmeyen DLL 'Leri kullanan uygulamalarla aynı azaltılan uygulamalarla aynı risk altında bulunur.  Örneğin, yönetilmeyen bir DLL 'nin `DllMain` giriş noktası `CoCreateInstance` com 'a sunulan yönetilen bir nesne almak için çağırırsa, bu, yükleyici kilidi içinde yönetilen kodu yürütmeye çalışır. .NET Framework sürüm 2,0 ve sonraki sürümlerde yükleyici kilit sorunları hakkında daha fazla bilgi için bkz. [karışık derlemeleri başlatma](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Çözüm  
 Visual C++ .NET 2002 ve Visual C++ .NET 2003 ' de, derleyici seçeneği ile derlenen dll 'Ler `/clr` yüklendiğinde belirleyici olmayan biçimde kilitlenmeye neden olabilir; bu sorun, karışık dll yükleme veya yükleyici kilit sorunu olarak adlandırılmıştı. Visual C++ 2005 ve üzeri sürümlerde, neredeyse tüm belirleyici olmayan ISM, karışık DLL yükleme işleminden kaldırılmıştır. Ancak, yükleyici kilidinin (belirleyici) meydana olabileceği birkaç senaryo vardır. Kalan yükleyici kilidi sorunları için nedenler ve çözümlerin ayrıntılı bir hesabı için bkz. [karışık derlemeler başlatma](/cpp/dotnet/initialization-of-mixed-assemblies). Bu konu, yükleyici kilit sorununuzu tanımlamadığı takdirde, yükleyici kilidinin neden gerçekleştiğini ve sorunu nasıl düzelteceğini belirlemek için iş parçacığının yığınını incelemeniz gerekir. Bu MDA ' i etkinleştiren iş parçacığı için yığın izlemesine bakın.  İş parçacığı, işletim sisteminin yükleyici kilidini tutarken yönetilen koda geçersiz şekilde çağrı yapmaya çalışıyor.  Büyük olasılıkla yığında bir DLL `DllMain` veya denk giriş noktası görürsünüz.  Bu tür bir giriş noktasının içinden yasal olarak yapabilecekleri, işletim sisteminin kuralları sınırlı değildir.  Bu kurallar, yönetilen yürütmeyi de halden daha fazla.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Genellikle, işlem içindeki birkaç iş parçacığı kilitlenir.  Bu iş parçacıklarından biri, çöp toplama gerçekleştirmekten sorumlu bir iş parçacığı olabilir, bu nedenle bu kilitlenme işlemin tamamına büyük bir etkiye sahip olabilir.  Ayrıca, derleme ve DLL 'Leri yükleme ve kaldırma, iş parçacıklarını başlatma veya durdurma gibi işletim sisteminin yükleyici kilidi gerektiren ek işlemleri de engeller.  
  
 Bazı Olağandışı durumlarda, erişim ihlalleri veya benzer sorunların, başlatılmadan önce çağrılan dll 'lerde tetiklenmesi de mümkündür.  
  
## <a name="output"></a>Çıktı  
 Bu MDA geçersiz bir yönetilen yürütmenin denenmekte olduğunu bildirir.  Yükleyici kilidinin neden gerçekleştiğini ve sorunu nasıl düzelteceğini öğrenmek için iş parçacığının yığınını incelemeniz gerekir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
