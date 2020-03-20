---
title: 'Azaltma: Yeni 64-bit JIT Derleyici'
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 883aaf032bde632b08f965d3450cfbea4feb8e65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181261"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a>Azaltma: Yeni 64-bit JIT Derleyici
.NET Framework 4.6 ile başlayarak, çalışma süresi tam zamanında derleme için yeni bir 64 bit JIT derleyicisi içerir. Bu değişiklik 32 bit JIT derleyicisi ile derleme etkilemez.  
  
## <a name="unexpected-behavior-or-exceptions"></a>Beklenmeyen davranış veya özel durumlar  
 Bazı durumlarda, yeni 64 bit JIT derleyicisi ile derleme bir çalışma zamanı özel durum veya eski 64-bit JIT derleyicisi tarafından derlenen kod yürütüldüğünde gözlenmeyen davranış sonuçları. Bilinen farklar şunlardır:  
  
> [!IMPORTANT]
> Bilinen tüm bu sorunlar .NET Framework 4.6.2 ile yayımlanan yeni 64 bit derleyicide ele alınmıştır. Çoğu, Windows Update ile birlikte verilen .NET Framework 4.6 ve 4.6.1'in hizmet sürümlerinde de ele alınmıştır. Windows sürümünüzün güncel olmasını sağlayarak veya .NET Framework 4.6.2'ye yükselterek bu sorunları ortadan kaldırabilirsiniz.  
  
- Belirli koşullar altında, bir unboxing <xref:System.NullReferenceException> işlemi bir in Release oluşturur en iyi duruma getirilmesi açık atabilir.  
  
- Bazı durumlarda, büyük bir yöntem gövdesinde üretim <xref:System.StackOverflowException>kodunun yürütülmesi bir.  
  
- Belirli koşullar altında, bir yönteme geçirilen yapılar, Sürüm yapılarındaki değer türleri yerine başvuru türleri olarak kabul edilir. Bu sorunun tezahürlerinden biri, koleksiyondaki tek tek öğelerin beklenmeyen bir sırada görünmesidir.  
  
- Belirli koşullar altında, <xref:System.UInt16> en iyi duruma getirilmesi etkinse değerlerin yüksek bit kümeleriyle karşılaştırılması yanlıştır.  
  
- Belirli koşullar altında, özellikle dizi değerlerini alırken, IL <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> yönergesi ile bellek başlatma yanlış bir değerle belleği başlatmayı sağlayabilir. Bu, işlenmemiş bir özel durum veya yanlış çıktı neden olabilir.  
  
- Belirli nadir koşullar altında, koşullu bit <xref:System.Boolean> testi yanlış değeri döndürebilir veya derleyici optimizasyonları etkinse bir özel durum atabilir.  
  
- Belirli koşullar altında, `if` bir `try` ifade bir blok girmeden önce ve `try` blok çıkışında bir durum için test etmek `catch` `finally` için kullanılırsa ve aynı koşul veya blok `if` tadisi sinde degistirilirse, yeni 64 bit JIT derleyicisi kodu en iyi duruma getirince durumu `catch` veya `finally` bloğu kaldırır. Sonuç olarak, ekstre `if` içindeki `catch` `finally` veya bloktaki kod koşulsuz olarak yürütülür.  
  
<a name="General"></a>
## <a name="mitigation-of-known-issues"></a>Bilinen sorunların azaltılması  
 Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak bunları ele alabilirsiniz:  
  
- .NET Framework 4.6.2'ye yükseltin. .NET Framework 4.6.2 ile birlikte eklenen yeni 64 bit derleyici, bilinen bu sorunların her birini giderir.  
  
- Windows Update çalıştırarak Windows sürümünüzün güncel olduğundan emin olun. .NET Framework 4.6 ve 4.6.1'deki hizmet güncelleştirmeleri, kutudan çıkarma işlemi dışında <xref:System.NullReferenceException> bu sorunların her birini giderir.  
  
- Eski 64 bit JIT derleyicisi ile derle. Bunun nasıl yapılacıla ilgili daha fazla bilgi için [diğer sorunların azaltımı](#Other) bölümüne bakın.  
  
<a name="Other"></a>
## <a name="mitigation-of-other-issues"></a>Diğer konuların azaltılması  
 Eski 64 bit derleyici ile derlenen kod ile yeni 64 bit JIT derleyicisi arasında veya uygulamanızın yeni 64 bit JIT derleyicisi ile derlenen hata ayıklama ve sürüm sürümleri arasında başka bir davranış farkıyla karşılaşırsanız, aşağıdakileri yapabilirsiniz: eski 64 bit JIT derleyicisi ile uygulamanızı derlemek için:  
  
- Uygulama başına olarak, uygulamanızın yapılandırma dosyasına [ \<LegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) öğesini ekleyebilirsiniz. Aşağıdaki devre dışı bırakma derlemesi yeni 64 bit JIT derleyicisi ile ve bunun yerine eski 64 bit JIT derleyicisi kullanır.  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- Kullanıcı başına bazda, kayıt defterinin `REG_DWORD` `useLegacyJit` `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtarına adlandırılmış bir değer ekleyebilirsiniz. 1 değeri eski 64 bit JIT derleyicisini sağlar; 0 değerini devre dışı kılabilir ve yeni 64 bit JIT derleyicisini etkinleştirin.  
  
- Makine başına olarak, kayıt defterinin `REG_DWORD` `useLegacyJit` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtarına adlandırılmış bir değer ekleyebilirsiniz. 1 değeri eski 64 bit JIT derleyicisini sağlar; 0 değerini devre dışı kılabilir ve yeni 64 bit JIT derleyicisini etkinleştirin.  
  
 Microsoft [Connect'te](https://connect.microsoft.com/VisualStudio)bir hata bildirerek sorun hakkında da bize bildirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
- [\<useLegacyJit> Element](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
