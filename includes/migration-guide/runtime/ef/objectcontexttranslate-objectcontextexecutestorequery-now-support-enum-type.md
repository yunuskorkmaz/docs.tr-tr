---
ms.openlocfilehash: 81992e57d7e92b4df92ce68870c0272d6cd5b220
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496153"
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

- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

<!--

#### Affected APIs

- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader)``
- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.Object[])``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])``

-->
