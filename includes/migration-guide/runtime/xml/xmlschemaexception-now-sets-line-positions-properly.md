---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235936"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="0b6f7-101">XmlSchemaException artık satır konumlarını düzgün ayarlar</span><span class="sxs-lookup"><span data-stu-id="0b6f7-101">XmlSchemaException now sets line positions properly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0b6f7-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0b6f7-102">Details</span></span>|<span data-ttu-id="0b6f7-103">Varsa <xref:System.Xml.Linq.LoadOptions.SetLineInfo> yük yönteme geçirilen değer ve bir doğrulama hatası oluşursa, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> özellikleri satır bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="0b6f7-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>|
|<span data-ttu-id="0b6f7-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="0b6f7-104">Suggestion</span></span>|<span data-ttu-id="0b6f7-105">Varsayar özel durum işleme kodları <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> değişmeyecek SetLineInfo XML yüklenirken kullanıldığında bu özellikler artık düzgün şekilde ayarlanır bu yana kümesi güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0b6f7-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>|
|<span data-ttu-id="0b6f7-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0b6f7-106">Scope</span></span>|<span data-ttu-id="0b6f7-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="0b6f7-107">Edge</span></span>|
|<span data-ttu-id="0b6f7-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0b6f7-108">Version</span></span>|<span data-ttu-id="0b6f7-109">4,5</span><span class="sxs-lookup"><span data-stu-id="0b6f7-109">4.5</span></span>|
|<span data-ttu-id="0b6f7-110">Tür</span><span class="sxs-lookup"><span data-stu-id="0b6f7-110">Type</span></span>|<span data-ttu-id="0b6f7-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="0b6f7-111">Runtime</span></span>|
|<span data-ttu-id="0b6f7-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0b6f7-112">Affected APIs</span></span>|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
