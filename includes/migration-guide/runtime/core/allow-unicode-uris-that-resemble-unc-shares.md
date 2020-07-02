---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621368"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
