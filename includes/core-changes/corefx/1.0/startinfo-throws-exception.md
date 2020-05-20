---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420440"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a><span data-ttu-id="64329-101">Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="64329-101">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>

<span data-ttu-id="64329-102"><xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType>Kodunuzun başlatmadığınız işlemlere yönelik özelliği okuma bir atar <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="64329-102">Reading the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start throws an <xref:System.InvalidOperationException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="64329-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="64329-103">Change description</span></span>

<span data-ttu-id="64329-104">.NET Framework, <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> kodunuzun başlatmadığınız işlemlere yönelik özelliğe erişim bir kukla <xref:System.Diagnostics.ProcessStartInfo> nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="64329-104">In .NET Framework, accessing the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start returns a dummy <xref:System.Diagnostics.ProcessStartInfo> object.</span></span> <span data-ttu-id="64329-105">Kukla nesne, hariç tüm özellikleri için varsayılan değerleri içerir <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> .</span><span class="sxs-lookup"><span data-stu-id="64329-105">The dummy object contains default values for all of its properties except <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables>.</span></span>

<span data-ttu-id="64329-106">.NET Core 1,0 ' den başlayarak, <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> başlatmadığınız bir işlemin özelliğini (çağırarak, çağırarak <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ) okuduğunuzda, bir oluşturulur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="64329-106">Starting in .NET Core 1.0, if you read the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for a process that you didn't start (that is, by calling <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>), an <xref:System.InvalidOperationException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="64329-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="64329-107">Version introduced</span></span>

<span data-ttu-id="64329-108">1.0</span><span class="sxs-lookup"><span data-stu-id="64329-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="64329-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="64329-109">Recommended action</span></span>

<span data-ttu-id="64329-110"><xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType>Kodunuzun başlamadığınız işlemlere yönelik özelliğe erişmeyin.</span><span class="sxs-lookup"><span data-stu-id="64329-110">Do not access the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start.</span></span> <span data-ttu-id="64329-111">Örneğin, tarafından döndürülen işlemlere yönelik bu özelliği okumayın <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="64329-111">For example, don't read this property for processes returned by <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="64329-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="64329-112">Category</span></span>

<span data-ttu-id="64329-113">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="64329-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="64329-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="64329-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
