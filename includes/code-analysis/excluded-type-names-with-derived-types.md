---
ms.openlocfilehash: 150882f3e4c9ff7abe811e09da94b8141de75778
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366833"
---
### <a name="exclude-specific-types-and-their-derived-types"></a>Belirli türleri ve bunların türetilmiş türlerini Dışla

Belirli türleri ve bunların türetilmiş türlerini analizden dışlayabilirsiniz. Örneğin, kuralın adlandırılmış türler ve türetilmiş türleri içindeki herhangi bir yöntemde çalıştırılmamalıdır `MyType` ve aşağıdaki anahtar-değer çiftini projenizdeki bir *. editorconfig* dosyasına ekleyin:

```ini
dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType
```

Seçenek değerindeki izin verilen sembol adı biçimleri (ile ayrılmış `|` ):

- Yalnızca tür adı (kapsayan tür veya ad alanından bağımsız olarak adı olan tüm türleri içerir)..
- Simgenin [belge kimliği biçimindeki](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings), isteğe bağlı ön ek olarak tam adlar `T:` .

Örnekler:

| Seçenek değeri | Özet |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType` | Tüm `MyType` türetilmiş türlerini ve tüm türetilmiş türlerini eşleştirir. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = MyType1|MyType2` | `MyType1`Ya da `MyType2` ve tüm türetilmiş türleri adlı tüm türleri eşleştirir. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS.MyType` | `MyType`Verilen tam adı ve tüm türetilmiş türlerini içeren belirli bir türle eşleşir. |
|`dotnet_code_quality.CAXXXX.excluded_type_names_with_derived_types = M:NS1.MyType1|M:NS2.MyType2` | Belirli türleri `MyType1` ve `MyType2` ilgili tam nitelikli adları ve tüm türetilmiş türlerini eşleştirir. |
