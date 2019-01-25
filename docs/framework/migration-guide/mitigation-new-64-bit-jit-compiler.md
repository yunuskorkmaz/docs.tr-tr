---
title: 'Azaltma: Yeni 64 bit JIT Derleyici'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d3eb82cf9bac1e40947fb78882d18c5f09b0092
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690091"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Azaltma: Yeni 64 bit JIT Derleyici
.NET Framework 4. 6 ile başlayarak, çalışma zamanı tam zamanında derleme için yeni bir 64 bit JIT derleyicisi içerir. Bu değişiklik, 32-bit JIT Derleyici ile derleme etkilemez.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Beklenmeyen davranış veya özel durumları  
 Bazı durumlarda, yeni 64 bit JIT Derleyici ile derleme çalışma zamanı özel veya eski 64 bit JIT derleyicisi tarafından derlenen kod yürütülürken uyulmuyor davranışı sonuçlanır. Bilinen farklar şunlardır:  
  
> [!IMPORTANT]
>  Bu bilinen sorunlara ilişkin tüm .NET Framework 4.6.2 ile sunulan yeni 64 bit derleyicide çözüldü. Çoğu, ayrıca Windows Update ile birlikte hizmet sürümlerinde .NET Framework 4.6 ve 4.6.1 çözüldü. Windows sürümünüz güncel veya .NET Framework 4.6.2 yükselterek sağlayarak bu sorunları ortadan kaldırabilir.  
  
-   Belirli koşullar altında bir kutudan çıkarma işlemi oluşturabilecek bir <xref:System.NullReferenceException> sürüm yapılarında açık iyileştirme.  
  
-   Bazı durumlarda, üretim kodunda büyük yöntem gövdesinin yürütülmesini oluşturabilecek bir <xref:System.StackOverflowException>.  
  
-   Belirli koşullar altında yayın içindeki değer türleri derlemeler yerine bir yönteme yapıları başvuru türleri olarak kabul edilir. Bu sorunun belirtileri bir koleksiyondaki tek tek öğelerin beklenmedik bir sırada göründüğünü biridir.  
  
-   Karşılaştırma işleminin belirli koşullar altında <xref:System.UInt16> bunların yüksek bit kümesi değerlerle iyileştirme etkinleştirildiğinde yanlış.  
  
-   Bazı koşullar altında özellikle zaman dizi başlatma değerleri, bellek başlatma tarafından <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL yönergesinin başlatmak bellek yanlış bir değere sahip. Bu, bir işlenmeyen özel durum veya yanlış çıkış sonuçlanabilir.  
  
-   Nadir bazı koşullarda koşullu bit test yanlış döndürebilir <xref:System.Boolean> değer veya derleyici iyileştirmeleri etkinleştirilip etkinleştirilmediğini bir özel durum.  
  
-   Belirli koşullar altında bir `if` deyimi girmeden önce koşulu test etmek için kullanılır bir `try` blok ve çıkın `try` blok ve aynı koşul içinde değerlendirilir `catch` veya `finally` blok, yeni 64 bit JIT Derleyici kaldırır `if` gelen koşul `catch` veya `finally` kodu en iyi duruma getirir, engelleyin. Sonuç olarak, içindeki kod `if` deyiminde `catch` veya `finally` blok koşulsuz olarak yürütülür.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Bilinen sorunlara ilişkin azaltma  
 Yukarıda listelenen bir sorunla karşılaşırsanız aşağıdakilerden birini yaparak karşılayabilirsiniz:  
  
-   .NET Framework 4.6.2 yükseltin. .NET Framework 4.6.2 dahil yeni bir 64 bit Derleyici her biri bu bilinen sorunları ele alır.  
  
-   Windows Update çalıştırarak Windows sürümünüz güncel olduğundan emin olun. .NET Framework 4.6 ve 4.6.1 için hizmet güncelleştirmeleri her dışında bu sorunları gidermek <xref:System.NullReferenceException> kutudan Çıkarma işleminde.  
  
-   Eski 64 bit JIT Derleyici ile derleyin. Bkz: [diğer sorunların azaltma](#Other) bölüm bunun nasıl yapılacağı hakkında daha fazla bilgi için.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Diğer sorunları riskini azaltma  
 Herhangi diğer davranıştaki farkı eski 64 bit derleyici ve yeni 64 bit JIT Derleyici ile derlenmiş kod arasında ya da uygulamanızın yeni bir 64 bit JIT Derleyici ile derlenmiş hata ayıklama ve yayın sürümleri arasında karşılaşırsanız, aşağıdakileri yapabilirsiniz eski 64 bit JIT Derleyici ile uygulamanızı derlemek için:  
  
-   Uygulama başına temelinde, eklediğiniz [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) uygulamanızın yapılandırma dosyasına öğesi. Aşağıdaki yeni 64 bit JIT Derleyici ile derleme devre dışı bırakır ve bunun yerine, eski 64 bit JIT Derleyici kullanır.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
-   Bir kullanıcı başına esasına göre ekleyebileceğiniz bir `REG_DWORD` değeri `useLegacyJit` için `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı. 1 değeri, eski 64 bit JIT Derleyici etkinleştirir; 0 değeri, devre dışı bırakır ve yeni 64 bit JIT Derleyici sağlar.  
  
-   Bir makine başına temelinde ekleyebileceğiniz bir `REG_DWORD` değeri `useLegacyJit` için `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` kayıt defteri anahtarı. 1 değeri, eski 64 bit JIT Derleyici etkinleştirir; 0 değeri, devre dışı bırakır ve yeni 64 bit JIT Derleyici sağlar.  
  
 Ayrıca sorun hakkında bir hata bildirimi tarafından bize [Microsoft Connect](https://connect.microsoft.com/VisualStudio).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [\<useLegacyJit > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
