---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009077"
---
### <a name="xml-parsing-changes"></a><span data-ttu-id="a81b5-101">XML ayrıştırma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a81b5-101">XML parsing changes</span></span>

| <span data-ttu-id="a81b5-102">Name</span><span class="sxs-lookup"><span data-stu-id="a81b5-102">Name</span></span>    | <span data-ttu-id="a81b5-103">Değer</span><span class="sxs-lookup"><span data-stu-id="a81b5-103">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="a81b5-104">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a81b5-104">Scope</span></span>   | <span data-ttu-id="a81b5-105">İkincil</span><span class="sxs-lookup"><span data-stu-id="a81b5-105">Minor</span></span>   |
| <span data-ttu-id="a81b5-106">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a81b5-106">Version</span></span> | <span data-ttu-id="a81b5-107">4.5.2</span><span class="sxs-lookup"><span data-stu-id="a81b5-107">4.5.2</span></span>   |
| <span data-ttu-id="a81b5-108">Tür</span><span class="sxs-lookup"><span data-stu-id="a81b5-108">Type</span></span>    | <span data-ttu-id="a81b5-109">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="a81b5-109">Runtime</span></span> |

#### <a name="details"></a><span data-ttu-id="a81b5-110">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a81b5-110">Details</span></span>

<span data-ttu-id="a81b5-111">Güvenlik nedenleriyle, XML ayrıştırma API 'lerinde aşağıdaki değişiklikler yapılmıştır:</span><span class="sxs-lookup"><span data-stu-id="a81b5-111">For security reasons, the following changes were introduced into XML parsing APIS:</span></span>

- <span data-ttu-id="a81b5-112"><xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> , başlatıldığında 10.000.000 olarak ayarlanır <xref:System.Xml.XmlReaderSettings> .</span><span class="sxs-lookup"><span data-stu-id="a81b5-112"><xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> is set to 10 million when <xref:System.Xml.XmlReaderSettings> is initialized.</span></span>
- <span data-ttu-id="a81b5-113"><xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType>`null`Varsayılan olarak olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a81b5-113"><xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> is set to `null` by default.</span></span>

> [!NOTE]
> <span data-ttu-id="a81b5-114"><xref:System.Xml.XmlReaderSettings> Tüm XML ayrıştırıcıları tarafından kullanılır, bu nedenle bu değişiklik, <xref:System.Xml.XmlReader> büyük/küçük harfe yardımcı olmakla aynı zamanda diğer senaryoları da etkiler.</span><span class="sxs-lookup"><span data-stu-id="a81b5-114"><xref:System.Xml.XmlReaderSettings> is used by all XML parsers, so while this change helps the <xref:System.Xml.XmlReader> case, it also affects other scenarios.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a81b5-115">Öneri</span><span class="sxs-lookup"><span data-stu-id="a81b5-115">Suggestion</span></span>

<span data-ttu-id="a81b5-116">Önceki davranışa geri dönmek için kayıt defterinde bir değer belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a81b5-116">To revert to the previous behavior, you can set a value in the registry.</span></span> <span data-ttu-id="a81b5-117">Kayıt defteri anahtarına adlı bir DWORD değeri ekleyin `EnableLegacyXmlSettings` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` ve değerini olarak ayarlayın `1` .</span><span class="sxs-lookup"><span data-stu-id="a81b5-117">Add a DWORD value named `EnableLegacyXmlSettings` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` registry key, and set its value to `1`.</span></span> <span data-ttu-id="a81b5-118">Bunun yerine HKEY_CURRENT_USER Hive kayıt defteri değerini de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a81b5-118">You can also add the registry value in the HKEY_CURRENT_USER hive instead.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a81b5-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a81b5-119">Affected APIs</span></span>

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

<span data-ttu-id="a81b5-120">Buna ek olarak, doğrudan veya dolaylı olarak bağımlı olan herhangi bir XML API 'SI <xref:System.Xml.XmlResolver> bundan etkilenir.</span><span class="sxs-lookup"><span data-stu-id="a81b5-120">In addition, any XML API that depends on <xref:System.Xml.XmlResolver>, either directly or indirectly, is affected.</span></span>

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
