---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009077"
---
### <a name="xml-parsing-changes"></a>XML ayrıştırma değişiklikleri

| Name    | Değer   |
|:--------|:--------|
| Kapsam   | İkincil   |
| Sürüm | 4.5.2   |
| Tür    | Çalışma Zamanı |

#### <a name="details"></a>Ayrıntılar

Güvenlik nedenleriyle, XML ayrıştırma API 'lerinde aşağıdaki değişiklikler yapılmıştır:

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> , başlatıldığında 10.000.000 olarak ayarlanır <xref:System.Xml.XmlReaderSettings> .
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType>`null`Varsayılan olarak olarak ayarlanır.

> [!NOTE]
> <xref:System.Xml.XmlReaderSettings> Tüm XML ayrıştırıcıları tarafından kullanılır, bu nedenle bu değişiklik, <xref:System.Xml.XmlReader> büyük/küçük harfe yardımcı olmakla aynı zamanda diğer senaryoları da etkiler.

#### <a name="suggestion"></a>Öneri

Önceki davranışa geri dönmek için kayıt defterinde bir değer belirleyebilirsiniz. Kayıt defteri anahtarına adlı bir DWORD değeri ekleyin `EnableLegacyXmlSettings` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` ve değerini olarak ayarlayın `1` . Bunun yerine HKEY_CURRENT_USER Hive kayıt defteri değerini de ekleyebilirsiniz.

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

Buna ek olarak, doğrudan veya dolaylı olarak bağımlı olan herhangi bir XML API 'SI <xref:System.Xml.XmlResolver> bundan etkilenir.

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
