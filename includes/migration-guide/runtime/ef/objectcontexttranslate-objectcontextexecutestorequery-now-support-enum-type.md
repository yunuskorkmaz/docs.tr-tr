---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620628"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext. Translate ve ObjectContext.ExecuteStoreQuery artık sabit listesi türünü destekliyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,0 ' de, <code>T</code> <code>ObjectContext.Translate</code> ve yöntemlerinin genel parametresi <code>ObjectContext.ExecuteStoreQuery</code> bir sabit listesi olamaz. Bu senaryo artık desteklenmektedir.

#### <a name="suggestion"></a>Öneri

.NET Framework 4,0 ' de bir sabit listesi türü üzerinde çevir veya ExecuteStoreQuery çağrılırsa, ' 0 ' döndürüldü. Bu davranış istenirse, çağrılar bir sabit 0 (veya Enum ile eşdeğer) ile değiştirilmelidir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
