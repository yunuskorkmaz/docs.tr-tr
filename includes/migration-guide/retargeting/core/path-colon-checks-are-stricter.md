---
ms.openlocfilehash: 6af63c0a58a3273aa98fa70f22e3637b481806b4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497387"
---
### <a name="path-colon-checks-are-stricter"></a>Yol noktalı virgül denetimleri daha sıkı

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ' de, daha önce desteklenmeyen yolları (hem length hem de biçiminde) desteklemeye yönelik bir dizi değişiklik yapılmıştır. Doğru sürücü ayırıcı (iki nokta üst üste) olup olmadığını denetler ve daha önceden toleranslı olan birkaç seçim yolu API 'sindeki bazı URI yollarını engellemeyi yan etkisi olan daha doğru yapılmıştır.

#### <a name="suggestion"></a>Öneri

Bir URI 'yi etkilenen API 'lere geçiriyorsanız, dizeyi önce geçerli bir yol olacak şekilde değiştirin.

- Şemayı, URL 'lerden el ile kaldırın (örneğin, URL 'lerden kaldırın `file://` ).

- URI 'yi <xref:System.Uri> sınıfa geçirin ve kullanın <xref:System.Uri.LocalPath> .

Alternatif olarak, `Switch.System.IO.UseLegacyPathHandling` AppContext anahtarını olarak ayarlayarak yeni yol normalleştirmesini devre dışı bırakabilirsiniz `true` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
