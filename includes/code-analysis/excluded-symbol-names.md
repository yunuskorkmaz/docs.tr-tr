---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366835"
---
### <a name="exclude-specific-symbols"></a>Belirli sembolleri Dışla

Tür ve yöntemler gibi belirli sembolleri analizden dışlayabilirsiniz. Örneğin, kuralın adlı tür içindeki herhangi bir kodda çalıştırılmamalıdır `MyType` , aşağıdaki anahtar-değer çiftini projenizdeki bir *. editorconfig* dosyasına ekleyin:

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

Seçenek değerindeki izin verilen sembol adı biçimleri (ile ayrılmış `|` ):

- Yalnızca sembol adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm sembolleri içerir).
- Simgenin [belge kimliği biçimindeki](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)tam adlar. Her sembol adı, metotlar için, `M:` `T:` türler için ve ad alanları gibi bir sembol türü ön eki gerektirir `N:` .
- `.ctor` oluşturucular ve `.cctor` statik oluşturucular için.

Örnekler:

| Seçenek değeri | Özet |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | Adlı tüm simgeleri eşleştirir `MyType` . |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | Ya da adlı tüm sembolleri `MyType1` eşler `MyType2` . |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | `MyMethod`Belirtilen tam imzaya sahip belirli bir yöntemle eşleşir. |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | Belirli yöntemlerle `MyMethod1` ve `MyMethod2` ilgili tam imzalarla eşleşir. |
