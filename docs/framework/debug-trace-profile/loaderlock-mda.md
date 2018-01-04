---
title: loaderLock MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks [.NET Framework]
- LoaderLock MDA
- MDAs (managed debugging assistants), loader locks
- managed debugging assistants (MDAs), loader locks
- operating system loader locks
- loader locks
- locks, threads
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2835f1fdbe2132feb929a5264d3b2772d8f66377
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="loaderlock-mda"></a>loaderLock MDA
`loaderLock` Yönetilen hata ayıklama Yardımcısı (MDA) Microsoft Windows işletim sistemi yükleyici kilidi tutan bir iş parçacığında yönetilen kod yürütme girişimlerini algılar.  Bu tür bir yürütme geçersiz çünkü Kilitlenmeler ve işletim sistemi yükleyicisi tarafından başlatılmış önce dll kullanmak için yol açabilir.  
  
## <a name="symptoms"></a>Belirtiler  
 İşletim sistemi yükleyici kilidi içinde kod yürütülürken en yaygın iş parçacıkları, ayrıca yükleyici kilidi gerektiren diğer Win32 işlevleri çağırmak çalışırken kilitlenme hatasıdır.  Bu tür işlevler örnekleri `LoadLibrary`, `GetProcAddress`, `FreeLibrary`, ve `GetModuleHandle`.  Uygulamayı doğrudan bu işlevler aranmayacağını; Ortak dil çalışma zamanı (CLR) gibi daha yüksek bir düzeyinde çağrının sonucu olarak bu işlevler çağırabilirsiniz <xref:System.Reflection.Assembly.Load%2A> veya ilk çağrıda bir platform çağırma yöntemi.  
  
 Başlangıç ve bitiş başka bir iş parçacığı için bekleyen bir iş parçacığı kilitlenmeleri de ortaya çıkabilir.  Bir iş parçacığı başlatır veya yürütme tamamlandıktan, etkilenen DLL'lere olayları teslim etmek için işletim sistemi yükleyici kilidi edinmeniz gerekir.  
  
 Son olarak, işletim sistemi yükleyicisi tarafından bu DLL'leri düzgün başlatılmamış önce DLL'leri çağrılarını gerçekleşebileceği durumlar vardır.  Tüm iş parçacıkları kilitlenmeyle ilgili yığınları inceleyerek koydu, kilitlenme hataları, bu MDA kullanmadan başlatılmamış DLL'lerin kullanımını tanılamak çok zor olabilir.  
  
## <a name="cause"></a>Sebep  
 İle bağlama .NET Framework sürüm 1.0 veya 1.1 genellikle özel dikkat, örneğin, alınmış sürece yükleyici kilidi içinde yönetilen kod çalıştırma denemesi için oluşturulmuş yönetilen ve yönetilmeyen C++ derlemeler karma **/NOENTRY**.
  
 .NET Framework sürüm 2.0 için yerleşik karışık yönetilen ve yönetilmeyen C++ derlemeler işletim sisteminin kurallarını ihlal yönetilmeyen DLL kullanan uygulamalar olarak aynı daha az risk altında olan bu sorunları için daha az açıktır.  Örneğin, yönetilmeyen DLL varsa'nın `DllMain` giriş noktası çağrıları `CoCreateInstance` COM gösterilen yönetilen bir nesne almak için yükleyici kilidi içinde yönetilen kod yürütme girişimi sonucudur. Yükleyici kilidi sorunlarını .NET Framework 2.0 ve sonraki sürümleri hakkında daha fazla bilgi için bkz: [karışık derlemeleri başlatma](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Çözüm  
 Visual C++ .NET 2002 ve Visual C++ .NET 2003'te DLL'leri ile derlenmiş `/clr` derleyici seçeneği belirleyici olmayan kilitlenme yüklendiğinde; bu sorunu karışık DLL yükleme veya yükleyici kilidi sorunu çağrıldı. Visual C++ 2005 ve sonraki sürümlerinde, neredeyse tüm gerekircilik karışık DLL yükleme işlemi kaldırılmıştır. Ancak, birkaç vardır hangi yükleyici kilidi oluşabilir (belirleyici biçimde) senaryoları kaldı. Nedenleri ve çözümlemeleri kalan yükleyici kilidi sorunlar için ayrıntılı bir hesabı için bkz: [karışık derlemeleri başlatma](/cpp/dotnet/initialization-of-mixed-assemblies). Bu konu, yükleyici kilidi sorunu tanımlamıyorsa, yükleyici kilidi neden oluştuğunu ve sorunun nasıl giderileceği belirlemek için iş parçacığının yığın incelemeniz gerekir. Bu MDA etkinleştirdi iş parçacığı için yığın izlemesi bakın.  İş parçacığı yasadışı işletim sistemi yükleyici kilidi tutarak yönetilen koda çağrı çalışıyor.  DLL büyük olasılıkla görürsünüz `DllMain` ya da eşdeğer giriş yığında noktası.  İşletim sisteminin yasal gelen içinde bu tür bir giriş noktası neler yapabileceğinizi kurallarını oldukça sınırlıdır.  Bu kural tüm yönetilen yürütme engellemek.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Genellikle, işlem içinde birkaç iş parçacığı kilitlenme.  Bu kilitlenme sürecinin tamamı üzerinde büyük bir etkisi olması için bir atık toplama gerçekleştirmek için sorumlu bir iş parçacığı büyük olasılıkla bu iş parçacığı biridir.  Ayrıca, yükleme ve kaldırma derlemeleri DLL'ler ve başlangıç veya iş parçacıklarını durdurma gibi işletim sistemi yükleyici kilidi gerektiren herhangi bir ek işlemler engeller.  
  
 Olağan dışı bazı durumlarda da erişim ihlalleri veya başlatılmış olması önce çağrılan DLL'lerde tetiklenmesi benzer sorunlar için mümkündür.  
  
## <a name="output"></a>Çıkış  
 Bu MDA geçersiz bir yönetilen yürütme yapılmaya çalışılan bildirir.  Yükleyici kilidi neden oluştuğunu ve sorunun nasıl giderileceği belirlemek için iş parçacığının yığın incelemeniz gerekir.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
