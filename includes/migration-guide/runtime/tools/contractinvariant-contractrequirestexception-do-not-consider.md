---
ms.openlocfilehash: 204fe32ec8b7fbaab89e37d7e761469212091728
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237911"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant veya Contract.Requires\<TException> String.IsNullOrEmpty saf olarak kabul etmeyin

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.1'i hedefleyen uygulamalar için, <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> metodu <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> çağıran için değişmez sözleşme veya ön koşul sözleşmesi varsa, rewriter &quot;derleyici uyarısı CC1036 yonttu: Yöntemde [Pure] olmadan 'System.String.IsNullOrWhteSpace(System.String)' yöntemine çağrı algılanır. &quot; Bu derleyici hatası yerine derleyici bir uyarıdır.|
|Öneri|Bu davranış [GitHub Sorunu #339](https://github.com/Microsoft/CodeContracts/issues/339)adresinde ele alınmıştır. Bu uyarıyı ortadan kaldırmak [için, GitHub'dan](https://github.com/Microsoft/CodeContracts/blob/master/README.md)Kod Sözleşmeleri aracının kaynak kodunun güncelleştirilmiş bir sürümünü indirebilir ve derleyebilirsiniz. İndirme bilgileri sayfanın alt kısmında bulunur.|
|Kapsam|İkincil|
|Sürüm|4.6.1|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
