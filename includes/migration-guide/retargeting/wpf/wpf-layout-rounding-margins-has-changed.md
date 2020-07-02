---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615775"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a><span data-ttu-id="81948-101">WPF düzen kenar boşluklarının yuvarlaması değiştirildi</span><span class="sxs-lookup"><span data-stu-id="81948-101">WPF layout rounding of margins has changed</span></span>

#### <a name="details"></a><span data-ttu-id="81948-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="81948-102">Details</span></span>

<span data-ttu-id="81948-103">Kenar boşluklarının yuvarlatılmış ve kenarlıkların yanı sıra bunların içindeki arka plan değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="81948-103">The way in which margins are rounded and borders and the background inside of them has changed.</span></span> <span data-ttu-id="81948-104">Bu değişikliğin sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="81948-104">As a result of this change:</span></span>

- <span data-ttu-id="81948-105">Öğelerin genişliği veya yüksekliği, en fazla bir piksel ile büyüyebilir veya küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="81948-105">The width or height of elements may grow or shrink by at most one pixel.</span></span>
- <span data-ttu-id="81948-106">Bir nesnenin yerleştirilmesi en çok bir piksel kadar hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="81948-106">The placement of an object can move by at most one pixel.</span></span>
- <span data-ttu-id="81948-107">Ortalanmış öğeler, en fazla bir piksel olarak orta veya yatay olarak devre dışı olabilir.</span><span class="sxs-lookup"><span data-stu-id="81948-107">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>
<span data-ttu-id="81948-108">Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4,6 ' i hedefleyen uygulamalar için etkindir.</span><span class="sxs-lookup"><span data-stu-id="81948-108">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="81948-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="81948-109">Suggestion</span></span>

<span data-ttu-id="81948-110">Bu değişiklik, yüksek DPA 'daki WPF denetimlerinin sağ veya alt bölümünün kırpılmasını ortadan kaldırmaya eğiliminden, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu yeni davranışı kabul edebilir `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="81948-110">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

<span data-ttu-id="81948-111">.NET Framework 4,6 ' i hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini tercih eden uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek yapabilir `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="81948-111">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| <span data-ttu-id="81948-112">Name</span><span class="sxs-lookup"><span data-stu-id="81948-112">Name</span></span>    | <span data-ttu-id="81948-113">Değer</span><span class="sxs-lookup"><span data-stu-id="81948-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="81948-114">Kapsam</span><span class="sxs-lookup"><span data-stu-id="81948-114">Scope</span></span>   | <span data-ttu-id="81948-115">İkincil</span><span class="sxs-lookup"><span data-stu-id="81948-115">Minor</span></span>       |
| <span data-ttu-id="81948-116">Sürüm</span><span class="sxs-lookup"><span data-stu-id="81948-116">Version</span></span> | <span data-ttu-id="81948-117">4.6</span><span class="sxs-lookup"><span data-stu-id="81948-117">4.6</span></span>         |
| <span data-ttu-id="81948-118">Tür</span><span class="sxs-lookup"><span data-stu-id="81948-118">Type</span></span>    | <span data-ttu-id="81948-119">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="81948-119">Retargeting</span></span> |
