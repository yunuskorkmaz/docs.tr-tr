---
ms.openlocfilehash: 0237c848d71150aaea1f9de4f4b16a0cbbc4ab3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615751"
---
### <a name="new-64-bit-jit-compiler-in-the-net-framework-46"></a>.NET Framework 4,6 ' de yeni 64-bit JıT derleyicisi

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' den başlayarak, tam zamanında derleme için yeni bir 64 bit JıT derleyicisi kullanılır. Bazı durumlarda, beklenmeyen bir özel durum oluşur veya farklı bir davranış, uygulamanın 32 bitlik derleyici veya daha eski 64 bit JıT derleyicisi kullanılarak çalıştırılmasından daha fazla gözlemlenmiştir. Bu değişiklik 32 bit JıT derleyicisini etkilemez. Bilinen farklılıklar şunları içerir:

- Belirli koşullar altında, bir kutudan çıkarma işlemi <xref:System.NullReferenceException> en iyi duruma getirme özelliği açık olan yayın yapıları oluşturabilir.
- Bazı durumlarda, büyük bir yöntem gövdesinde üretim kodunun yürütülmesi bir oluşturabilir <xref:System.StackOverflowException> .
- Belirli koşullar altında, bir yönteme geçirilen yapılar, yayın Derlemeleriyle değer türleri yerine başvuru türleri olarak değerlendirilir. Bu sorunun bildirimli bir şekilde, bir koleksiyondaki tek öğelerin beklenmeyen bir sırada görünmesine neden olur.
- Belirli koşullar altında, <xref:System.UInt16> en iyi duruma getirme etkinse değerlerin yüksek bit kümesiyle karşılaştırılması yanlış olur.
- Belirli koşullar altında, özellikle dizi değerlerini başlatırken, Il yönergesi tarafından bellek başlatma <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> yanlış bir değerle belleği başlatabilir. Bu, işlenmemiş bir özel durum ya da yanlış çıkışa neden olabilir.
- Bazı nadir koşullarda, koşullu bir bit testi yanlış <xref:System.Boolean> değeri döndürebilir veya derleyici iyileştirmeleri etkinse bir özel durum oluşturabilir.
- Belirli koşullarda, bir `if` ifadeyi bir blok girmeden ve bloğundan çıkışta bir koşulu test etmek için kullanılırsa `try` `try` ve veya bloğunda aynı koşul değerlendirilirse, `catch` `finally` Yeni 64 bit JIT derleyicisi `if` kodu en `catch` `finally` iyi duruma getirirken koşulu veya bloğundan kaldırır. Sonuç olarak, `if` veya bloğundaki deyimin içindeki kod koşulsuz olarak `catch` `finally` yürütülür.

#### <a name="suggestion"></a>Öneri

**Bilinen sorunların risk azaltma** <br/> Yukarıda listelenen sorunlarla karşılaşırsanız, aşağıdakilerden birini yaparak bunları ele alabilirsiniz:

- .NET Framework 4.6.2 ' ye yükseltin. .NET Framework 4.6.2 ile birlikte sunulan yeni 64 bitlik derleyici, bu bilinen sorunların her birini ele alır.
- Windows Update çalıştırarak Windows sürümünüzün güncel olduğundan emin olun. .NET Framework 4,6 ve 4.6.1 için hizmet güncelleştirmeleri, kutudan çıkarma işlemi dışında bu sorunların her birini ele verir <xref:System.NullReferenceException> .
- Daha eski 64 bit JıT derleyicisi ile derleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için **diğer sorunların hafifletme** bölümüne bakın.
**Diğer sorunları azaltma** <br/> Daha eski 64-bit derleyicisi ile derlenen kod ve yeni 64-bit JIT derleyicisi ile derlenmiş kod arasında başka bir farklılık yaşarsanız veya hem yeni 64-bit JıT derleyicisi ile derlenen uygulamanızın hata ayıklama ve yayın sürümleri arasında, uygulamanızı daha eski bir 64-bit JIT derleyicisi ile derlemek için aşağıdakileri yapabilirsiniz :

- Uygulama başına temelinde, [<](~/docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) öğesini uygulamanızın yapılandırma dosyasına ekleyebilirsiniz. Aşağıdakiler, yeni 64-bit JıT derleyicisi ile derlemeyi devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.

    ```xml
    <?xml version ="1.0"?>
    <configuration>
      <runtime>
       <useLegacyJit enabled="1" />
      </runtime>
    </configuration>
    ```

- Kullanıcı başına temelinde, `REG_DWORD` `useLegacyJit` kayıt defteri anahtarına adlı bir değer ekleyebilirsiniz `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` . 1 değeri, eski 64-bit JıT derleyicisini sunar; 0 değeri devre dışı bırakır ve yeni 64 bit JıT derleyicisini etkinleştirilir.
- Makine başına temelinde, `REG_DWORD` `useLegacyJit` kayıt defteri anahtarına adlı bir değer ekleyebilirsiniz `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` . Değeri, `1` eski 64 BIT JIT derleyicisini etkinleştirmesine izin vermez; bir değeri `0` bunu devre dışı bırakır ve yeni 64 bit JIT derleyicisini sunar.
Ayrıca, [Microsoft Connect](https://connect.microsoft.com/VisualStudio)'te bir hata bildirerek sorun hakkında bilgi sahibi olalım.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |
