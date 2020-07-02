---
ms.openlocfilehash: 29c66edfeb1690199aac39b9c3076d161b2075d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621441"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract. sabit veya sözleşme. \<TException> Için String. IsNullOrEmpty 'ın saf olmasını gerektirmeyin

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.1 ' i hedefleyen uygulamalar için, <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> veya önkoşul sözleşmesi için olan sabit sözleşme <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> yöntemini çağırırsa, Rewriter derleyicinin uyarı CC1036: &quot; ' System. String. ısnullorwhtespace (System. String) ' metoduna [saf] olmadan çağrı algıladı. &quot; Bu, derleyici hatası yerine bir derleyici uyarısına sahiptir.

#### <a name="suggestion"></a>Öneri

Bu davranış, [GitHub sorun #339](https://github.com/Microsoft/CodeContracts/issues/339)' de giderilmiştir. Bu uyarıyı ortadan kaldırmak için, [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md)'Dan kod sözleşmeleri aracı için kaynak kodun güncelleştirilmiş bir sürümünü indirebilir ve derleyebilirsiniz. İndirme bilgileri sayfanın alt kısmında bulunur.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6.1|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
