---
title: loaderLock MDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a70b8c3509b785d70b041b449c759e7994e5984
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148726"
---
# <a name="loaderlock-mda"></a>loaderLock MDA
`loaderLock` Yönetilen hata ayıklama Yardımcısı (MDA) Microsoft Windows işletim sistemi yükleyici kilidi tutan bir iş parçacığında yönetilen kodu yürütmek için girişimleri algılar.  Böyle bir yürütme, Kilitlenmeler ve işletim sistemi yükleyicisi tarafından başlatılmış olması önce dll kullanmak için neden olabileceği için geçersizdir.  
  
## <a name="symptoms"></a>Belirtiler  
 İşletim sistemi yükleyici kilidi içinde kod yürütülürken en yaygın iş parçacıkları yükleyici kilidi gerektiren diğer Win32 işlevlerini çağırmaya çalışırken kilitlenme hatasıdır.  Bu tür işlevler örnekleri `LoadLibrary`, `GetProcAddress`, `FreeLibrary`, ve `GetModuleHandle`.  Uygulamayı doğrudan bu işlevler çağırmamanız; Ortak dil çalışma zamanı (CLR), bu işlevler gibi daha yüksek bir düzeyinde çağrının sonucu olarak çağırabilirsiniz <xref:System.Reflection.Assembly.Load%2A> veya ilk çağrıda bir platform çağırma yöntemi.  
  
 Bir iş parçacığı başlangıç ve bitiş başka bir iş parçacığı için bekliyorsa kilitlenmeleri de oluşabilir.  Bir iş parçacığı başlatıldığında veya yürütme tamamlandıktan sonra işletim sistemi yükleyici kilidi etkilenen DLL'lerin olayları teslim etmeyi edinmeniz gerekir.  
  
 Son olarak, bu DLL'leri işletim sistemi yükleyicisi tarafından düzgün şekilde başlatıldığından önce DLL'leri çağırıyor burada oluşabilecek durumlar vardır.  Tüm iş parçacıkları kilitlenmeyle ilgili yığını inceleyerek koydu, kilitlenme hataların, bu mda'nın kullanmadan başlatılmamış DLL'lerin kullanımına tanılamak oldukça zor.  
  
## <a name="cause"></a>Sebep  
 Bağlama ile .NET Framework sürümleri 1.0 veya 1.1 genellikle önemi, örneğin, alınmış sürece, yönetilen kod yükleyici kilidi içinde çalıştırma denemesi için oluşturulan yönetilen veya yönetilmeyen C++ karışık derlemeler **/NOENTRY**.
  
 .NET Framework 2.0 sürümünde oluşturulmuş karışık yönetilen veya yönetilmeyen C++ derlemeler işletim sisteminin kurallarını ihlal yönetilmeyen DLL'ler kullanan uygulamalar olarak aynı daha az risk altında olan bu sorunları için daha az açıktır.  Örneğin, yönetilmeyen DLL'ın `DllMain` giriş noktası çağrıları `CoCreateInstance` COM kullanıma sunulan bir yönetilen nesne almak için yönetilen kod yükleyici kilidi içinde yürütme girişimi sonucudur. .NET Framework sürüm 2.0 ve sonraki yükleyici kilidi sorunlar hakkında daha fazla bilgi için bkz. [karışık derlemeleri başlatma](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Çözüm  
 Visual C++ .NET 2002 ve Visual C++ .NET 2003'te, DLL'ler ile derlenmiş `/clr` derleyici seçeneği belirleyici olmayan şekilde kilitlenme yüklendiğinde; bu sorunu karışık DLL yükleme veya yükleyici kilidi sorunu çağrıldı. Visual C++ 2005 ve sonraki sürümlerinde, neredeyse tüm gerekircilik karışık DLL yükleme işlemi kaldırıldı. Ancak, birkaç vardır senaryoları için hangi yükleyici kilidi oluşabilir (belirleyici) kaldı. Nedenleri ve çözümlemeleri kalan yükleyici kilidi sorunlarında ayrıntılı hesabı için bkz: [karışık derlemeleri başlatma](/cpp/dotnet/initialization-of-mixed-assemblies). Bu konu, yükleyici kilidi sorununuzu tanımlamaz, yükleyici kilidi neden oluştuğunu ve sorunun nasıl giderileceği belirlemek için iş parçacığının yığınını incelemek sahip. Bu mda'nın etkinleştirilmiş iş parçacığı için yığın izlemesi bakın.  İş parçacığı, yasa dışı işletim sistemi yükleyici kilidi tutuluyken yönetilen koda çağrı yapmak çalışıyor.  Bir DLL'nin büyük olasılıkla görürsünüz `DllMain` veya eşdeğer girişi yığın üzerine gelin.  İşletim sisteminin yasal gelen içinde bu tür bir giriş noktası yapabilecekleriniz kuralları oldukça sınırlıdır.  Bu kurallar herhangi bir yönetilen yürütme kullanımını.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Genellikle, işlem içinde birden çok iş parçacığı kilitlenme.  Bu iş parçacıkları birini bir iş parçacığı bu kilitlenme işlem üzerinde önemli bir etkiye sahip olabilir, böylece bir çöp toplama yapmaktan sorumlu olması olasıdır.  Ayrıca, yükleme ve kaldırma derlemeleri veya DLL'leri ve başlangıç veya iş parçacıklarını durdurma gibi işletim sistemi yükleyici kilidi gerektiren herhangi bir ek işlem engel olur.  
  
 Olağan dışı bazı durumlarda da erişim ihlalleri veya başlatılmış olması önce çağrılan DLL'lerde tetiklenmesi için benzer sorunlar için mümkündür.  
  
## <a name="output"></a>Çıkış  
 Bu MDA, geçersiz bir yönetilen yürütme yapılmaya çalışılan bildirir.  Yükleyici kilidi neden oluştuğunu ve sorunun nasıl giderileceği belirlemek için iş parçacığı yığınının incelemeniz gerekir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
