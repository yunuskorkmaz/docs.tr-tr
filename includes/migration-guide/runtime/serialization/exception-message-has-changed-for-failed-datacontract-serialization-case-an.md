---
ms.openlocfilehash: 8d0404c728231f596500653d556e3be6fcc20c2c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497647"
---
### <a name="exception-message-has-changed-for-failed-datacontract-serialization-in-case-of-an-unknown-type"></a>Bilinmeyen bir tür durumunda başarısız olan DataContract serileştirmesi için özel durum iletisi değişti

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' den başlayarak, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName> ' bilinen türler ' eksik olması nedeniyle bir veya seri hale getirilemez veya seri durumdan çıkarılamazsa verilen özel durum iletisi, açıklığa kavuşturuldu.

#### <a name="suggestion"></a>Öneri

Uygulamalar belirli özel durum iletilerine bağlı olmamalıdır. Bir uygulama bu iletiye bağımlıysa, bunu yeni iletiyi beklemek üzere güncelleştirin ya da (tercihen) yalnızca özel durum türüne göre değiştirin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Runtime.Serialization.Json.DataContractJsonSerializerSettings)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.String)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.String,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Runtime.Serialization.DataContractSerializerSettings)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.String,System.String)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type})>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)>
- <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)>

<!--

#### Affected APIs

- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Runtime.Serialization.Json.DataContractJsonSerializerSettings)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.String)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.String,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)`
- `M:System.Runtime.Serialization.Json.DataContractJsonSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Boolean)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Runtime.Serialization.DataContractSerializerSettings)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.String,System.String)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type})`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.String,System.String,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate)`
- `M:System.Runtime.Serialization.DataContractSerializer.#ctor(System.Type,System.Xml.XmlDictionaryString,System.Xml.XmlDictionaryString,System.Collections.Generic.IEnumerable{System.Type},System.Int32,System.Boolean,System.Boolean,System.Runtime.Serialization.IDataContractSurrogate,System.Runtime.Serialization.DataContractResolver)`

-->
