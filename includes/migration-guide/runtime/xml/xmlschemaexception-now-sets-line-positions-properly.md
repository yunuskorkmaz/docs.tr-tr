---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805240"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="34876-101">XmlSchemaException artık satır konumlarını düzgün ayarlar</span><span class="sxs-lookup"><span data-stu-id="34876-101">XmlSchemaException now sets line positions properly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="34876-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="34876-102">Details</span></span>|<span data-ttu-id="34876-103">Varsa <xref:System.Xml.Linq.LoadOptions.SetLineInfo> yük yönteme geçirilen değer ve bir doğrulama hatası oluşursa, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> özellikleri satır bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="34876-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>|
|<span data-ttu-id="34876-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="34876-104">Suggestion</span></span>|<span data-ttu-id="34876-105">Varsayar özel durum işleme kodları <xref:System.Xml.Schema.XmlSchemaException.LineNumber> ve <xref:System.Xml.Schema.XmlSchemaException.LinePosition> değişmeyecek SetLineInfo XML yüklenirken kullanıldığında bu özellikler artık düzgün şekilde ayarlanır bu yana kümesi güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="34876-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>|
|<span data-ttu-id="34876-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="34876-106">Scope</span></span>|<span data-ttu-id="34876-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="34876-107">Edge</span></span>|
|<span data-ttu-id="34876-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="34876-108">Version</span></span>|<span data-ttu-id="34876-109">4,5</span><span class="sxs-lookup"><span data-stu-id="34876-109">4.5</span></span>|
|<span data-ttu-id="34876-110">Tür</span><span class="sxs-lookup"><span data-stu-id="34876-110">Type</span></span>|<span data-ttu-id="34876-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="34876-111">Runtime</span></span>|
|<span data-ttu-id="34876-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="34876-112">Affected APIs</span></span>|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
