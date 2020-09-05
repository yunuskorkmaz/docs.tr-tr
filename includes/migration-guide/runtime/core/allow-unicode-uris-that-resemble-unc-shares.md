---
ms.openlocfilehash: 1047f4028697a73741470d1aac8b3aeed37be217
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496812"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>UNC Paylaşımlarına benzeyen URI 'Lerinde Unicode 'a izin ver

#### <a name="details"></a>Ayrıntılar

' De <xref:System.Uri?displayProperty=fullName> , hem UNC paylaşma adı hem de Unicode karakterler içeren bir dosya URI 'si oluşturmak, artık geçersiz iç duruma sahip BIR URI ile sonuçlanmaz. Bu davranış yalnızca aşağıdakilerin tümü doğru olduğunda değişir:<ul><li>URI şemaya sahiptir <code>file:</code> ve ardından dört veya daha fazla eğik çizgi gelir.</li><li>Ana bilgisayar adı, alt çizgi veya ayrılmış olmayan başka bir sembol ile başlar.</li><li>URI Unicode karakterler içeriyor.</li></ul>

#### <a name="suggestion"></a>Öneri

Bir şekilde Unicode içeren URI 'Ler ile çalışan uygulamalar, UNC Paylaşımlarına yönelik başvurulara izin vermek için bu davranışı çalıp. Bunun yerine bu uygulamalar kullanılmalıdır <xref:System.Uri.IsUnc> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.7.2|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Uri?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Uri`

-->
