---
ms.openlocfilehash: 086dac69d085d070511fcfd5820bd2644ee4598e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497230"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="6965f-101">Marshal. SizeOf ve Marshal. PtrToStructure aşırı yüklemeleri dinamik kodu Böl</span><span class="sxs-lookup"><span data-stu-id="6965f-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="6965f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6965f-102">Details</span></span>

<span data-ttu-id="6965f-103">.NET Framework 4.5.1 ' den başlayarak,,,,, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601> <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> veya <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> , (örneğin, Windows PowerShell, IronPython veya C# dinamik anahtar sözcüğü aracılığıyla) dinamik olarak bağlama, <code>MethodInvocationExceptions</code> Bu yöntemlerin yeni aşırı yüklemeleri eklendiğinden, komut dosyası altyapılarına belirsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="6965f-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6965f-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="6965f-104">Suggestion</span></span>

<span data-ttu-id="6965f-105">Hangi aşırı yüklemenin kullanılması gerektiğini açıkça belirtmek için betikleri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="6965f-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="6965f-106">Bu, genellikle yöntemlerin tür parametreleri olarak açıkça atama yoluyla yapılabilir <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="6965f-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="6965f-107">Daha fazla ayrıntı ve soruna geçici çözüm örnekleri için [Bu bağlantıya](https://support.microsoft.com/kb/2909958/) bakın.</span><span class="sxs-lookup"><span data-stu-id="6965f-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="6965f-108">Name</span><span class="sxs-lookup"><span data-stu-id="6965f-108">Name</span></span>    | <span data-ttu-id="6965f-109">Değer</span><span class="sxs-lookup"><span data-stu-id="6965f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6965f-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6965f-110">Scope</span></span>   |<span data-ttu-id="6965f-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="6965f-111">Minor</span></span>|
|<span data-ttu-id="6965f-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6965f-112">Version</span></span>|<span data-ttu-id="6965f-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6965f-113">4.5.1</span></span>|
|<span data-ttu-id="6965f-114">Tür</span><span class="sxs-lookup"><span data-stu-id="6965f-114">Type</span></span>|<span data-ttu-id="6965f-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="6965f-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6965f-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6965f-116">Affected APIs</span></span>

<span data-ttu-id="6965f-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="6965f-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
