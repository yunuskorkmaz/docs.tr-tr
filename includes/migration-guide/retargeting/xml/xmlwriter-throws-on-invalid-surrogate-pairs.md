---
ms.openlocfilehash: f87b70708398226516ab5eac32c24a9fc2c1106b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615781"
---
### <a name="xmlwriter-throws-on-invalid-surrogate-pairs"></a><span data-ttu-id="28b77-101">XmlWriter, geçersiz vekil çiftlerine atar</span><span class="sxs-lookup"><span data-stu-id="28b77-101">XmlWriter throws on invalid surrogate pairs</span></span>

#### <a name="details"></a><span data-ttu-id="28b77-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="28b77-102">Details</span></span>

<span data-ttu-id="28b77-103">.NET Framework 4.5.2 veya önceki sürümleri hedefleyen uygulamalar için, özel durum geri dönüş işleme kullanarak geçersiz bir yedek çifti yazmak her zaman bir özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="28b77-103">For apps that target the .NET Framework 4.5.2 or previous versions, writing an invalid surrogate pair using exception fallback handling does not always throw an exception.</span></span> <span data-ttu-id="28b77-104">.NET Framework 4,6 ' i hedefleyen uygulamalar için geçersiz bir yedek çifti yazma girişimi bir oluşturur <xref:System.ArgumentException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="28b77-104">For apps that target the .NET Framework 4.6, attempting to write an invalid surrogate pair throws an <xref:System.ArgumentException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="28b77-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="28b77-105">Suggestion</span></span>

<span data-ttu-id="28b77-106">Gerekirse, bu kesmeyi .NET Framework 4.5.2 veya daha önceki bir sürümü hedefleyerek önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="28b77-106">If necessary, this break can be avoided by targeting the .NET Framework 4.5.2 or earlier.</span></span> <span data-ttu-id="28b77-107">Alternatif olarak, geçersiz yedek çiftleri yazmadan önce geçerli XML 'e önceden işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="28b77-107">Alternatively, invalid surrogate pairs can be pre-processed into valid xml prior to writing them.</span></span>

| <span data-ttu-id="28b77-108">Name</span><span class="sxs-lookup"><span data-stu-id="28b77-108">Name</span></span>    | <span data-ttu-id="28b77-109">Değer</span><span class="sxs-lookup"><span data-stu-id="28b77-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="28b77-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="28b77-110">Scope</span></span>   | <span data-ttu-id="28b77-111">Edge</span><span class="sxs-lookup"><span data-stu-id="28b77-111">Edge</span></span>        |
| <span data-ttu-id="28b77-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="28b77-112">Version</span></span> | <span data-ttu-id="28b77-113">4.6</span><span class="sxs-lookup"><span data-stu-id="28b77-113">4.6</span></span>         |
| <span data-ttu-id="28b77-114">Tür</span><span class="sxs-lookup"><span data-stu-id="28b77-114">Type</span></span>    | <span data-ttu-id="28b77-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="28b77-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="28b77-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="28b77-116">Affected APIs</span></span>

- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeString(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteAttributeStringAsync(System.String,System.String,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCData(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCDataAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteChars(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCharsAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteComment(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteCommentAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRef(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteEntityRefAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstruction(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteProcessingInstructionAsync(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRaw(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.Char[],System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteRawAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteString(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteStringAsync(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntity(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteSurrogateCharEntityAsync(System.Char,System.Char)?displayProperty=nameWithType>
- <xref:System.Xml.XmlWriter.WriteValue(System.String)?displayProperty=nameWithType>
