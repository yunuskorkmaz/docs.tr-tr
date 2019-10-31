---
title: 'Risk azaltma: yeni 64-bit JıT derleyicisi'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: cad61bd86080fc21f0a47ef92b1908d6e7588a23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126238"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Risk azaltma: yeni 64-bit JıT derleyicisi
.NET Framework 4,6 ' den başlayarak, çalışma zamanı tam zamanında derleme için yeni bir 64 bit JıT derleyicisi içerir. Bu değişiklik, 32 bit JıT derleyicisi ile derlemeyi etkilemez.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Beklenmeyen davranış veya özel durumlar  
 Bazı durumlarda, yeni 64-bit JıT derleyicisi ile derleme, çalışma zamanı özel durumu veya eski 64 bit JıT derleyicisi tarafından derlenen kodu yürütürken gözlemlenmemiş davranışlar ile sonuçlanır. Bilinen farklılıklar şunları içerir:  
  
> [!IMPORTANT]
> Bu bilinen sorunların tümü, .NET Framework 4.6.2 ile yayınlanan yeni 64 bit derleyicide ele alındı. Çoğu Ayrıca, Windows Update dahil edilen .NET Framework 4,6 ve 4.6.1 hizmet sürümlerinde de giderilmiştir. Windows sürümünüzün güncel olmasını sağlayarak veya 4.6.2 .NET Framework yükselterek bu sorunları ortadan kaldırabilirsiniz.  
  
- Belirli koşullar altında, bir kutudan çıkarma işlemi en iyi duruma getirme özelliği açık olan yayın yapılarından <xref:System.NullReferenceException> oluşturabilir.  
  
- Bazı durumlarda, büyük bir yöntem gövdesinde üretim kodunun yürütülmesi <xref:System.StackOverflowException>oluşturabilir.  
  
- Belirli koşullar altında, bir yönteme geçirilen yapılar, yayın Derlemeleriyle değer türleri yerine başvuru türleri olarak değerlendirilir. Bu sorunun bildirimli bir şekilde, bir koleksiyondaki tek öğelerin beklenmeyen bir sırada görünmesine neden olur.  
  
- Belirli koşullar altında, en iyi duruma getirme etkinse <xref:System.UInt16> değerlerinin yüksek bit kümesiyle karşılaştırılması yanlış olur.  
  
- Belirli koşullar altında, özellikle dizi değerlerini başlatırken, <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> Il yönergesi tarafından bellek başlatma, hatalı bir değerle belleği başlatabilir. Bu, işlenmemiş bir özel durum ya da yanlış çıkışa neden olabilir.  
  
- Bazı nadir koşullarda, koşullu bir bit testi yanlış <xref:System.Boolean> değerini döndürebilir veya derleyici iyileştirmeleri etkinse bir özel durum oluşturabilir.  
  
- Belirli koşullar altında, bir `if` bildiri, bir `try` bloğunu girmeden önce bir koşulu test etmek için kullanılırsa ve `try` bloğundan çıkışta, `catch` veya `finally` bloğunda aynı koşul değerlendirilir Yeni 64-bit JıT derleyicisi, kodu en iyi duruma getirirken `catch` veya `finally` bloğundan `if` koşulunu kaldırır. Sonuç olarak, `catch` veya `finally` bloğundaki `if` deyimin içindeki kod koşulsuz olarak yürütülür.  
  
<a name="General"></a>   
## <a name="mitigation-of-known-issues"></a>Bilinen sorunların risk azaltma  
 Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak bunları ele alabilirsiniz:  
  
- .NET Framework 4.6.2 ' ye yükseltin. .NET Framework 4.6.2 ile birlikte sunulan yeni 64 bitlik derleyici, bu bilinen sorunların her birini ele alır.  
  
- Windows Update çalıştırarak Windows sürümünüzün güncel olduğundan emin olun. .NET Framework 4,6 ve 4.6.1 için hizmet güncelleştirmeleri, kutudan çıkarma işleminde <xref:System.NullReferenceException> hariç, bu sorunlardan her birini adresleyen.  
  
- Daha eski 64 bit JıT derleyicisi ile derleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için [diğer sorunların hafifletme](#Other) bölümüne bakın.  
  
<a name="Other"></a>   
## <a name="mitigation-of-other-issues"></a>Diğer sorunları azaltma  
 Eski 64 bit derleyicisi ile derlenen kod ve yeni 64-bit JıT derleyicisi ile derlenmiş kod arasındaki davranışta veya yeni 64-bit JıT derleyicisi ile derlenen uygulamanızın hata ayıklama ve yayın sürümleri arasında başka bir farklılık yaşarsanız, aşağıdakileri yapabilirsiniz Uygulamanızı eski 64 bit JıT derleyicisi ile derlemek için:  
  
- Uygulama başına temelinde, [\<useLegacyJit >](../configure-apps/file-schema/runtime/uselegacyjit-element.md) öğesini uygulamanızın yapılandırma dosyasına ekleyebilirsiniz. Aşağıdakiler, yeni 64-bit JıT derleyicisi ile derlemeyi devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Kullanıcı başına temelinde, kayıt defterinin `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtarına `useLegacyJit` adlı `REG_DWORD` bir değer ekleyebilirsiniz. 1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.  
  
- Makine başına temelinde, kayıt defterinin `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtarına `useLegacyJit` adlı `REG_DWORD` bir değer ekleyebilirsiniz. 1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.  
  
 Ayrıca, [Microsoft Connect](https://connect.microsoft.com/VisualStudio)'te bir hata bildirerek sorun hakkında bilgi sahibi olalım.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](runtime-changes-in-the-net-framework-4-6.md)
- [\<useLegacyJit > öğesi](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
