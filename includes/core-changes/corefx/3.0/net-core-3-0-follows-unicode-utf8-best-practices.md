---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568230"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3,0 hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirirken Unicode en iyi yöntemlerini izler

<xref:System.Text.UTF8Encoding> sınıfı, bir bayt karakter dönüştürme işlemi sırasında hatalı biçimlendirilmiş bir UTF-8 bayt dizisiyle karşılaştığında, bu diziyi çıkış dizesindeki bir ' ' (U + FFFD DEĞIŞTIRME KARAKTERI) karakteriyle değiştirecek. .NET Core 3,0, .NET Core 'un önceki sürümlerinden ve .NET Framework dönüştürme işlemi sırasında bu değişikliği gerçekleştirmek için en iyi Unicode yöntemi izleyerek farklıdır.

Bu, yeni <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> ve <xref:System.Text.Rune?displayProperty=nameWithType> türleri dahil olmak üzere .NET genelinde UTF-8 işlemesini geliştirmenin daha büyük bir çaba parçasıdır. <xref:System.Text.UTF8Encoding> türüne, Yeni tanıtılan türlerle tutarlı bir çıkış üretmesi için, bir hata işleme mekanizması sağlanmadı.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,0 ile başlayarak, baytları karakterlere dönüştürme sırasında <xref:System.Text.UTF8Encoding> sınıfı, Unicode en iyi uygulamalarına göre karakter değiştirme işlemini gerçekleştirir. Kullanılan değiştirme mekanizması, _U + FFFD Substitution alt bölümlerinin_başlığı altında bulunan başlık Içindeki [Unicode standart, sürüm 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) ile açıklanmıştır.

Bu davranış _yalnızca_ , giriş bayt dizisi hatalı biçimlendirilmiş UTF-8 verileri içerdiğinde geçerlidir. Ek olarak, <xref:System.Text.UTF8Encoding> örneği `throwOnInvalidBytes: true` ile oluşturulmuşsa (bkz. [UTF8Encoding Oluşturucu belgeleri] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, `UTF8Encoding` örneği U + FFFD değişimi gerçekleştirmek yerine geçersiz giriş üzerinde throw 'e devam edecektir.

Aşağıda, bu değişikliğin geçerli bir 3 baytlık giriş ile etkisi gösterilmektedir:

|Hatalı biçimlendirilmiş 3 baytlık giriş|.NET Core 3,0 öncesi çıkış|.NET Core 3,0 ile başlayan çıkış|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]` (2 karakterlik çıkış)| `[ FFFD FFFD FFFD ]` (3 karakterlik çıkış)|

Bu 3-char çıktısı, daha önce bağlantılı Unicode standart PDF 'nin _3-9 tablosuna_ göre tercih edilen çıktıdır.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Geliştiricinin bölümünde herhangi bir eylem gerekmez.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
