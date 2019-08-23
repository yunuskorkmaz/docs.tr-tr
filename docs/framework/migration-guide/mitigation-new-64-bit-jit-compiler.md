---
title: Mayı Yeni 64-bit JıT derleyicisi
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6df750872e90572b00cdf427461b4a9782c47d63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968518"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Mayı Yeni 64-bit JıT derleyicisi
.NET Framework 4,6 ' den başlayarak, çalışma zamanı tam zamanında derleme için yeni bir 64 bit JıT derleyicisi içerir. Bu değişiklik, 32 bit JıT derleyicisi ile derlemeyi etkilemez.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Beklenmeyen davranış veya özel durumlar  
 Bazı durumlarda, yeni 64-bit JıT derleyicisi ile derleme, çalışma zamanı özel durumu veya eski 64 bit JıT derleyicisi tarafından derlenen kodu yürütürken gözlemlenmemiş davranışlar ile sonuçlanır. Bilinen farklılıklar şunları içerir:  
  
> [!IMPORTANT]
> Bu bilinen sorunların tümü, .NET Framework 4.6.2 ile yayınlanan yeni 64 bit derleyicide ele alındı. Çoğu Ayrıca, Windows Update dahil edilen .NET Framework 4,6 ve 4.6.1 hizmet sürümlerinde de giderilmiştir. Windows sürümünüzün güncel olmasını sağlayarak veya 4.6.2 .NET Framework yükselterek bu sorunları ortadan kaldırabilirsiniz.  
  
- Belirli koşullar altında, bir kutudan çıkarma işlemi en iyi <xref:System.NullReferenceException> duruma getirme özelliği açık olan yayın yapıları oluşturabilir.  
  
- Bazı durumlarda, büyük bir yöntem gövdesinde üretim kodunun yürütülmesi bir <xref:System.StackOverflowException>oluşturabilir.  
  
- Belirli koşullar altında, bir yönteme geçirilen yapılar, yayın Derlemeleriyle değer türleri yerine başvuru türleri olarak değerlendirilir. Bu sorunun bildirimli bir şekilde, bir koleksiyondaki tek öğelerin beklenmeyen bir sırada görünmesine neden olur.  
  
- Belirli koşullar altında, en iyi duruma <xref:System.UInt16> getirme etkinse değerlerin yüksek bit kümesiyle karşılaştırılması yanlış olur.  
  
- Belirli koşullar altında, özellikle dizi değerlerini başlatırken, <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> Il yönergesi tarafından bellek başlatma yanlış bir değerle belleği başlatabilir. Bu, işlenmemiş bir özel durum ya da yanlış çıkışa neden olabilir.  
  
- Bazı nadir koşullarda, koşullu bir bit testi yanlış <xref:System.Boolean> değeri döndürebilir veya derleyici iyileştirmeleri etkinse bir özel durum oluşturabilir.  
  
- Belirli koşullar `if` altında, bir ifade bir `try` blok girmeden önce bir koşulu test etmek için kullanılırsa ve `try` bloğundan çıkıldığında, `catch` veya `finally` bloğunda aynı koşul değerlendirilirse, yeni 64-bit JIT derleyicisi, `if` `catch` kodu en iyi duruma getirirken `finally` koşulu veya bloğundan kaldırır. Sonuç olarak, `if` `catch` veya `finally` bloğundaki deyimin içindeki kod koşulsuz olarak yürütülür.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Bilinen sorunların risk azaltma  
 Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak bunları ele alabilirsiniz:  
  
- .NET Framework 4.6.2 ' ye yükseltin. .NET Framework 4.6.2 ile birlikte sunulan yeni 64 bitlik derleyici, bu bilinen sorunların her birini ele alır.  
  
- Windows Update çalıştırarak Windows sürümünüzün güncel olduğundan emin olun. .NET Framework 4,6 ve 4.6.1 için hizmet güncelleştirmeleri, <xref:System.NullReferenceException> kutudan çıkarma işlemi dışında bu sorunların her birini ele verir.  
  
- Daha eski 64 bit JıT derleyicisi ile derleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için [diğer sorunların hafifletme](#Other) bölümüne bakın.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Diğer sorunları azaltma  
 Eski 64 bit derleyicisi ile derlenen kod ve yeni 64-bit JıT derleyicisi ile derlenmiş kod arasındaki davranışta veya yeni 64-bit JıT derleyicisi ile derlenen uygulamanızın hata ayıklama ve yayın sürümleri arasında başka bir farklılık yaşarsanız, aşağıdakileri yapabilirsiniz Uygulamanızı eski 64 bit JıT derleyicisi ile derlemek için:  
  
- Uygulama başına temelinde, [ \<useLegacyJit >](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) öğesini uygulamanızın yapılandırma dosyasına ekleyebilirsiniz. Aşağıdakiler, yeni 64-bit JıT derleyicisi ile derlemeyi devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Kullanıcı başına temelinde, kayıt defteri `REG_DWORD` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtarına adlı `useLegacyJit` bir değer ekleyebilirsiniz. 1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.  
  
- Makine başına temelinde, kayıt defteri `REG_DWORD` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtarına adlı `useLegacyJit` bir değer ekleyebilirsiniz. 1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.  
  
 Ayrıca, [Microsoft Connect](https://connect.microsoft.com/VisualStudio)'te bir hata bildirerek sorun hakkında bilgi sahibi olalım.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
- [\<useLegacyJit > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)
