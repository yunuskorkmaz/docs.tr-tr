---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616115"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a><span data-ttu-id="c125d-101">Kullanımdan kaldırıldı Teattribute, WinMD senaryolarında hem kullanımdan kaldırıldı hem de kullanımdan kaldırıldı olarak dışarı aktarmalar</span><span class="sxs-lookup"><span data-stu-id="c125d-101">ObsoleteAttribute exports as both ObsoleteAttribute and DeprecatedAttribute in WinMD scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="c125d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c125d-102">Details</span></span>

<span data-ttu-id="c125d-103">Bir Windows meta veri kitaplığı (. winmd dosyası) oluşturduğunuzda, <xref:System.ObsoleteAttribute?displayProperty=fullName> öznitelik hem <xref:System.ObsoleteAttribute?displayProperty=fullName> ve [Windows. Foundation. kullanımdan](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)kaldırıldı ' olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="c125d-103">When you create a Windows Metadata library (.winmd file), the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute is exported as both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c125d-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="c125d-104">Suggestion</span></span>

<span data-ttu-id="c125d-105">Özniteliği kullanan mevcut kaynak kodun yeniden derlenmesi, <xref:System.ObsoleteAttribute?displayProperty=fullName> Bu kodu C++/CX veya JavaScript 'ten kullanırken uyarılar oluşturabilir. <xref:System.ObsoleteAttribute?displayProperty=fullName> yönetilen derlemelerdeki koda hem hem de [Windows. Foundation. kullanımdan kaldırıldı.](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)</span><span class="sxs-lookup"><span data-stu-id="c125d-105">Recompilation of existing source code that uses the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute may generate warnings when consuming that code from C++/CX or JavaScript.We do not recommend applying both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) to code in managed assemblies; it may result in build warnings.</span></span>

| <span data-ttu-id="c125d-106">Name</span><span class="sxs-lookup"><span data-stu-id="c125d-106">Name</span></span>    | <span data-ttu-id="c125d-107">Değer</span><span class="sxs-lookup"><span data-stu-id="c125d-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c125d-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c125d-108">Scope</span></span>   | <span data-ttu-id="c125d-109">Edge</span><span class="sxs-lookup"><span data-stu-id="c125d-109">Edge</span></span>        |
| <span data-ttu-id="c125d-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c125d-110">Version</span></span> | <span data-ttu-id="c125d-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="c125d-111">4.5.1</span></span>       |
| <span data-ttu-id="c125d-112">Tür</span><span class="sxs-lookup"><span data-stu-id="c125d-112">Type</span></span>    | <span data-ttu-id="c125d-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="c125d-113">Retargeting</span></span> |
