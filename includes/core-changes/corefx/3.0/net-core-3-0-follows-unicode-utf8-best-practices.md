---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721131"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a>Hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirme Unicode yönergelerine uyar

Sınıf, <xref:System.Text.UTF8Encoding> bir bayt karakter dönüştürme işlemi sırasında hatalı biçimlendirilmiş BIR UTF-8 bayt dizisiyle karşılaştığında, bu diziyi çıkış dizesindeki ' ' (U + FFFD DEĞIŞTIRME karakteri) karakteriyle değiştirir. .NET Core 3,0, .NET Core 'un önceki sürümlerinden ve .NET Framework dönüştürme işlemi sırasında bu değişikliği gerçekleştirmek için en iyi Unicode yöntemi izleyerek farklıdır.

Bu, yeni ve türleri dahil olmak üzere .NET genelinde UTF-8 işlemesini geliştirmenin daha büyük bir çaba parçasıdır <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> <xref:System.Text.Rune?displayProperty=nameWithType> . <xref:System.Text.UTF8Encoding>Türe, Yeni tanıtılan türlerle tutarlı bir çıkış üretmesi için, bu tür gelişmiş hata işleme mekanizması verildi.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ile başlayarak, baytları karakterlere dönüştürme sırasında <xref:System.Text.UTF8Encoding> sınıf, Unicode en iyi uygulamalarına göre karakter değiştirme işlemini gerçekleştirir. Kullanılan değiştirme mekanizması, _U + FFFD Substitution alt bölümlerinin_başlığı altında bulunan başlık Içindeki [Unicode standart, sürüm 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) ile açıklanmıştır.

Bu davranış _yalnızca_ , giriş bayt dizisi hatalı biçimlendirilmiş UTF-8 verileri içerdiğinde geçerlidir. Ek olarak, <xref:System.Text.UTF8Encoding> örneği ile oluşturulmuşsa `throwOnInvalidBytes: true` , `UTF8Encoding` örnek U + FFFD yerini almak yerine geçersiz giriş üzerinde throw olmaya devam edecektir. Oluşturucu hakkında daha fazla bilgi için `UTF8Encoding` bkz <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> ..

Aşağıdaki tabloda, bu değişikliğin geçersiz bir 3 bayt girişi ile etkisi gösterilmektedir:

| Hatalı biçimlendirilmiş 3 baytlık giriş | .NET Core 3,0 öncesi çıkış          | .NET Core 3,0 ile başlayan çıkış        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | `[ FFFD FFFD ]`(2 karakterlik çıkış) | `[ FFFD FFFD FFFD ]`(3 karakterlik çıkış) |

3-char çıktısı, daha önce bağlantılı Unicode standart PDF 'nin _3-9 tablosuna_ göre tercih edilen çıktıdır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Geliştiricinin bölümünde herhangi bir eylem gerekmez.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
