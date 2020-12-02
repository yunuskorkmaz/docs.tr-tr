---
ms.openlocfilehash: 639cd13978cc33bd7c4524a17e92d566404bbaea
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477644"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract. sabit veya sözleşme. \<TException> Için String. IsNullOrEmpty 'ın saf olmasını gerektirmeyin

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.1 ' i hedefleyen uygulamalar için, <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> veya önkoşul sözleşmesi için olan sabit sözleşme, <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> yöntemi çağırırsa, Rewriter derleyici uyarısı CC1036: &quot; ' System. String. IsNullOrWhiteSpace (System. String) ' metoduna [saf] yöntemi olmadan çağrı algıladı. &quot; Bu, derleyici hatası yerine bir derleyici uyarısına sahiptir.

#### <a name="suggestion"></a>Öneri

Bu davranış, [GitHub sorun #339](https://github.com/Microsoft/CodeContracts/issues/339)' de giderilmiştir. Bu uyarıyı ortadan kaldırmak için, [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md)'Dan kod sözleşmeleri aracı için kaynak kodun güncelleştirilmiş bir sürümünü indirebilir ve derleyebilirsiniz. İndirme bilgileri sayfanın alt kısmında bulunur.

| Ad    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->
