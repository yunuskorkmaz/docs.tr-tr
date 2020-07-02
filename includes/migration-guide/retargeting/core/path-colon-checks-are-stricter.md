---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614715"
---
### <a name="path-colon-checks-are-stricter"></a>Yol noktalı virgül denetimleri daha sıkı

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ' de, daha önce desteklenmeyen yolları (hem length hem de biçiminde) desteklemeye yönelik bir dizi değişiklik yapılmıştır. Uygun sürücü ayırıcı (iki nokta üst üste) olup olmadığını denetler ve daha doğru bir şekilde, birkaç seçim yolu API 'SI ile kullanım dışı olarak kullanıldıkları yerde bazı URI yollarını engellemenin yan etkisi vardı.

#### <a name="suggestion"></a>Öneri

Bir URI 'yi etkilenen API 'lere geçiriyorsanız, dizeyi önce geçerli bir yol olacak şekilde değiştirin.<ul><li>Şemayı, URL 'lerden el ile kaldırın (örn. `file://` URL 'lerden Kaldır)

- URI 'yi <xref:System.Uri> sınıfa geçirin ve kullanın<xref:System.Uri.LocalPath>

Alternatif olarak, `Switch.System.IO.UseLegacyPathHandling` AppContext anahtarını true olarak ayarlayarak yeni yol normalleştirmesini devre dışı bırakabilirsiniz.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
