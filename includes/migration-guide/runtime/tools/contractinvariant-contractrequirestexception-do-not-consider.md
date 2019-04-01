---
ms.openlocfilehash: 91e09e71a32bb6d410ff52a97a8d14384ee3a5f1
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58467095"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant veya Contract.Requires\<TException > String.ısnullorempty saf olmasını dikkate almaz

|   |   |
|---|---|
|Ayrıntılar|Değişmez değer için Sözleşme, .NET Framework 4.6.1'i hedefleyen uygulamalar için <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> veya önkoşulu sözleşmesi <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> çağrıları <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> yöntem, rewriter yayar CC1036 uyarı derleyici: &quot;Algılanan yöntemine çağrı <xref:System.String.IsNullOrWhiteSpace%2A?displayProperty=nameWithType> [saf] olmadan yönteminde.&quot; Derleyici Hatası yerine uyarı derleyicisidir.|
|Öneri|Bu davranış te çözüm getirilen [GitHub sorun #339](https://github.com/Microsoft/CodeContracts/issues/339). Bu uyarıyı kaldırmak için indirebilir ve kaynak kodu kod sözleşmeleri aracı için güncelleştirilmiş bir sürümünü derlemek [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). İndirme bilgileri sayfasının altında bulunur.|
|Kapsam|İkincil|
|Sürüm|4.6.1|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

