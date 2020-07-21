---
title: 'Risk azaltma: yeni 64-bit JıT derleyicisi'
description: .NET Framework 4,6 ' de bulunan yeni 64-bit JıT derleyicisi ve derleme sırasında oluşabilecek beklenmeyen davranış veya özel durumlar hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: f059cbdd3b2a66ac8a668b7b8a80d9ad1551fa64
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475235"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Risk azaltma: yeni 64-bit JıT derleyicisi
.NET Framework 4,6 ' den başlayarak, çalışma zamanı tam zamanında derleme için yeni bir 64 bit JıT derleyicisi içerir. Bu değişiklik, 32 bit JıT derleyicisi ile derlemeyi etkilemez.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Beklenmeyen davranış veya özel durumlar  
 Bazı durumlarda, yeni 64-bit JıT derleyicisi ile derleme, çalışma zamanı özel durumu veya eski 64 bit JıT derleyicisi tarafından derlenen kodu yürütürken gözlemlenmemiş davranışlar ile sonuçlanır. Bilinen farklılıklar şunları içerir:  
  
> [!IMPORTANT]
> Bu bilinen sorunların tümü, .NET Framework 4.6.2 ile yayınlanan yeni 64 bit derleyicide ele alındı. Çoğu Ayrıca, Windows Update dahil edilen .NET Framework 4,6 ve 4.6.1 hizmet sürümlerinde de giderilmiştir. Windows sürümünüzün güncel olmasını sağlayarak veya 4.6.2 .NET Framework yükselterek bu sorunları ortadan kaldırabilirsiniz.  
  
- Belirli koşullar altında, bir kutudan çıkarma işlemi <xref:System.NullReferenceException> en iyi duruma getirme özelliği açık olan yayın yapıları oluşturabilir.  
  
- Bazı durumlarda, büyük bir yöntem gövdesinde üretim kodunun yürütülmesi bir oluşturabilir <xref:System.StackOverflowException> .  
  
- Belirli koşullar altında, bir yönteme geçirilen yapılar, yayın Derlemeleriyle değer türleri yerine başvuru türleri olarak değerlendirilir. Bu sorunun bildirimli bir şekilde, bir koleksiyondaki tek öğelerin beklenmeyen bir sırada görünmesine neden olur.  
  
- Belirli koşullar altında, <xref:System.UInt16> en iyi duruma getirme etkinse değerlerin yüksek bit kümesiyle karşılaştırılması yanlış olur.  
  
- Belirli koşullar altında, özellikle dizi değerlerini başlatırken, Il yönergesi tarafından bellek başlatma <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> yanlış bir değerle belleği başlatabilir. Bu, işlenmemiş bir özel durum ya da yanlış çıkışa neden olabilir.  
  
- Bazı nadir koşullarda, koşullu bir bit testi yanlış <xref:System.Boolean> değeri döndürebilir veya derleyici iyileştirmeleri etkinse bir özel durum oluşturabilir.  
  
- Belirli koşullarda, bir `if` ifadeyi bir blok girmeden ve bloğundan çıkışta bir koşulu test etmek için kullanılırsa `try` `try` ve veya bloğunda aynı koşul değerlendirilirse, `catch` `finally` Yeni 64 bit JIT derleyicisi `if` kodu en `catch` `finally` iyi duruma getirirken koşulu veya bloğundan kaldırır. Sonuç olarak, `if` veya bloğundaki deyimin içindeki kod koşulsuz olarak `catch` `finally` yürütülür.  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a>Bilinen sorunların risk azaltma  
 Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak bunları ele alabilirsiniz:  
  
- .NET Framework 4.6.2 ' ye yükseltin. .NET Framework 4.6.2 ile birlikte sunulan yeni 64 bitlik derleyici, bu bilinen sorunların her birini ele alır.  
  
- Windows Update çalıştırarak Windows sürümünüzün güncel olduğundan emin olun. .NET Framework 4,6 ve 4.6.1 için hizmet güncelleştirmeleri, kutudan çıkarma işlemi dışında bu sorunların her birini ele verir <xref:System.NullReferenceException> .  
  
- Daha eski 64 bit JıT derleyicisi ile derleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için [diğer sorunların hafifletme](#Other) bölümüne bakın.  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a>Diğer sorunları azaltma  
 Daha eski 64-bit derleyicisi ile derlenen kod ve yeni 64-bit JIT derleyicisi ile derlenmiş kod arasında başka bir farklılık yaşarsanız veya hem yeni 64-bit JıT derleyicisi ile derlenen uygulamanızın hata ayıklama ve yayın sürümleri arasında, uygulamanızı daha eski bir 64-bit JIT derleyicisi ile derlemek için aşağıdakileri yapabilirsiniz :  
  
- Uygulama başına temelinde, [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) öğesini uygulamanızın yapılandırma dosyasına ekleyebilirsiniz. Aşağıdakiler, yeni 64-bit JıT derleyicisi ile derlemeyi devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Kullanıcı başına temelinde, `REG_DWORD` `useLegacyJit` kayıt defteri anahtarına adlı bir değer ekleyebilirsiniz `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` . 1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.  
  
- Makine başına temelinde, `REG_DWORD` `useLegacyJit` kayıt defteri anahtarına adlı bir değer ekleyebilirsiniz `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` . 1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.  
  
 Ayrıca, [Microsoft Connect](https://connect.microsoft.com/VisualStudio)'te bir hata bildirerek sorun hakkında bilgi sahibi olalım.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
- [\<useLegacyJit>Dosyalarında](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
