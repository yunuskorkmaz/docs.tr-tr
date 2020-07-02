---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620586"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="6a99e-101">Marshal. SizeOf ve Marshal. PtrToStructure aşırı yüklemeleri dinamik kodu Böl</span><span class="sxs-lookup"><span data-stu-id="6a99e-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="6a99e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6a99e-102">Details</span></span>

<span data-ttu-id="6a99e-103">.NET Framework 4.5.1 ' den başlayarak,,,,, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601> <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> veya <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> , (örneğin, Windows PowerShell, IronPython veya C# dinamik anahtar sözcüğü aracılığıyla) dinamik olarak bağlama, <code>MethodInvocationExceptions</code> Bu yöntemlerin yeni aşırı yüklemeleri eklendiğinden, komut dosyası altyapılarına belirsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a99e-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6a99e-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="6a99e-104">Suggestion</span></span>

<span data-ttu-id="6a99e-105">Hangi aşırı yüklemenin kullanılması gerektiğini açıkça belirtmek için betikleri güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="6a99e-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="6a99e-106">Bu, genellikle yöntemlerin tür parametreleri olarak açıkça atama yoluyla yapılabilir <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="6a99e-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="6a99e-107">Daha fazla ayrıntı ve soruna geçici çözüm örnekleri için [Bu bağlantıya](https://support.microsoft.com/kb/2909958/) bakın.</span><span class="sxs-lookup"><span data-stu-id="6a99e-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="6a99e-108">Name</span><span class="sxs-lookup"><span data-stu-id="6a99e-108">Name</span></span>    | <span data-ttu-id="6a99e-109">Değer</span><span class="sxs-lookup"><span data-stu-id="6a99e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6a99e-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6a99e-110">Scope</span></span>   |<span data-ttu-id="6a99e-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="6a99e-111">Minor</span></span>|
|<span data-ttu-id="6a99e-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6a99e-112">Version</span></span>|<span data-ttu-id="6a99e-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6a99e-113">4.5.1</span></span>|
|<span data-ttu-id="6a99e-114">Tür</span><span class="sxs-lookup"><span data-stu-id="6a99e-114">Type</span></span>|<span data-ttu-id="6a99e-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="6a99e-115">Runtime</span></span>|
