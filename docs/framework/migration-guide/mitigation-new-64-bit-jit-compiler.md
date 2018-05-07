---
title: 'Azaltma: Yeni 64-bit JIT derleme'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4edce9558cdbdd5937aa12866077210a91ee8494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Azaltma: Yeni 64-bit JIT derleme
.NET Framework 4.6 ile başlayarak, çalışma zamanı tam zamanında derleme için yeni bir 64-bit JIT Derleyici içerir. Bu değişiklik, 32-bit JIT derleyicisi ile derleme etkilemez.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Beklenmeyen davranışları ya da özel durumlar  
 Bazı durumlarda, bir çalışma zamanı özel veya eski 64-bit JIT derleyicisi tarafından derlenen kod yürütülürken gözlenir değil davranışı derleme yeni 64-bit JIT derleyicisi ile sonuçlanır. Bilinen farklar aşağıdakileri içerir:  
  
> [!IMPORTANT]
>  Bu bilinen sorunların tümünü .NET Framework 4.6.2 ile yayımlanan yeni 64 bit derleyici giderilmiştir. Çoğu ayrıca Windows Update ile dahil edilen hizmet sürümlerinde .NET Framework 4.6 ve 4.6.1 giderilmiştir. Windows sürümünüz güncel, .NET Framework 4.6.2 yükselterek mi sağlayarak bu sorunları ortadan kaldırabilirsiniz.  
  
-   Belirli koşullar altında kutudan çıkarma işlemi atabilir bir <xref:System.NullReferenceException> yayın derlemelerinde açık iyileştirme.  
  
-   Bazı durumlarda, üretim kodunda büyük yöntem gövdesi yürütülmesi atabilir bir <xref:System.StackOverflowException>.  
  
-   Değer türleri sürümdeki derlemeler yerine belirli koşullar altında bir yönteme geçirilen yapıları başvuru türleri olarak kabul edilir. Bu sorun belirtileri bir koleksiyon içindeki öğeleri beklenmeyen bir düzende görünür biridir.  
  
-   Karşılaştırması belirli koşullar altında <xref:System.UInt16> değerleri kendi yüksek bit kümesiyle iyileştirme etkinleştirilirse yanlış.  
  
-   Belirli koşullar altında özellikle zaman dizi başlatma değerleri, bellek başlatma tarafından <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL yönerge belleğe yanlış bir değere sahip başlatmak. Bu da bir işlenmeyen özel durum ya da hatalı çıktı neden olabilir.  
  
-   Nadir belirli koşullar altında koşullu bit test yanlış döndürebilir <xref:System.Boolean> değer veya derleyici iyileştirmesi etkinleştirilmişse bir özel durum.  
  
-   Belirli koşullar altında bir `if` deyimi için bir koşul girmeden önce sınamak için kullanılan bir `try` blok ve çıkın `try` bloğu ve aynı koşul olarak değerlendirildiği `catch` veya `finally` bloğu, yeni 64 bit JIT Derleyici kaldırır `if` gelen koşul `catch` veya `finally` kod iyileştirir olduğunda engelleme. Sonuç olarak, içindeki kod `if` deyiminde `catch` veya `finally` blok koşulsuz olarak yürütülür.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Bilinen sorunlar azaltma  
 Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak karşılayabilirsiniz:  
  
-   .NET Framework 4.6.2'ye yükseltin. .NET Framework 4.6.2 dahil yeni 64 bit Derleyici her bu bilinen sorunları giderir.  
  
-   Windows Update çalıştırarak Windows sürümünüz güncel olduğundan emin olun. .NET Framework 4.6 ve 4.6.1 için hizmet güncelleştirmeleri her dışında bu sorunların adres <xref:System.NullReferenceException> kutudan Çıkarma işleminde.  
  
-   Eski 64-bit JIT derleyicisi ile derleyin. Bkz: [azaltma diğer sorunların](#Other) bunun nasıl yapılacağı hakkında daha fazla bilgi için bölüm.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Diğer sorunlar azaltma  
 Herhangi diğer bir fark davranış eski 64 bit derleyici ve yeni 64-bit JIT derleyicisi ile derlenmiş kod arasında ya da her ikisini de yeni 64-bit JIT derleyicisi ile derlenen hata ayıklama ve yayın sürümleri arasında uygulamanızı karşılaşırsanız, şunları yapabilirsiniz eski 64-bit JIT derleyicisi ile uygulamanızı derlemek için:  
  
-   Bir uygulama başına temelinde eklediğiniz [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) , uygulamanızın yapılandırma dosyasına öğesi. Aşağıdaki yeni 64-bit JIT derleyicisi ile derlemeyi devre dışı bırakır ve bunun yerine eski 64-bit JIT Derleyici kullanır.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   Bir kullanıcı başına temelinde eklediğiniz bir `REG_DWORD` adlı değeri `useLegacyJit` için `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı. 1 değeri eski 64-bit JIT derleyicisi tanır; 0 değeri, devre dışı bırakır ve yeni 64-bit JIT Derleyici sağlar.  
  
-   Bir makine başına temelinde eklediğiniz bir `REG_DWORD` adlı değeri `useLegacyJit` için `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı. 1 değeri eski 64-bit JIT derleyicisi tanır; 0 değeri, devre dışı bırakır ve yeni 64-bit JIT Derleyici sağlar.  
  
 Ayrıca bize sorun hakkında bir hata bildirimi tarafından bilmeniz [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 [\<useLegacyJit > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
