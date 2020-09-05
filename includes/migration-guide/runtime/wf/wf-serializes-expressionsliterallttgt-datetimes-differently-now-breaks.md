---
ms.openlocfilehash: 06424c4fa40343a881356c20003300f65e93efbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497297"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="76477-101">WF deyimleri seri hale getirir. sabit değerli &lt; T &gt; DateTimeS Now (özel xaml ayrıştırıcılarını keser)</span><span class="sxs-lookup"><span data-stu-id="76477-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="76477-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="76477-102">Details</span></span>

<span data-ttu-id="76477-103">İlişkili <xref:System.Windows.Markup.ValueSerializer> nesne, <xref:System.DateTime?displayProperty=fullName> <xref:System.DateTimeOffset?displayProperty=fullName> ikinci ve bileşenleri sıfır olmayan bir veya nesnesi <xref:System.DateTime.Millisecond?displayProperty=fullName> (bir değer için), özelliği de <xref:System.DateTime?displayProperty=fullName> <xref:System.DateTime.Kind> bir dize yerine özellik öğesi söz dizimine belirtilmemiş olarak dönüştürecek.</span><span class="sxs-lookup"><span data-stu-id="76477-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="76477-104">Bu değişiklik <xref:System.DateTime?displayProperty=fullName> , ve <xref:System.DateTimeOffset?displayProperty=fullName> değerlerinin yuvarlak olarak değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="76477-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="76477-105">Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="76477-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="76477-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="76477-106">Suggestion</span></span>

<span data-ttu-id="76477-107">Bu değişiklik <xref:System.DateTime?displayProperty=fullName> , ve <xref:System.DateTimeOffset?displayProperty=fullName> değerlerinin yuvarlak olarak değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="76477-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="76477-108">Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="76477-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="76477-109">Name</span><span class="sxs-lookup"><span data-stu-id="76477-109">Name</span></span>    | <span data-ttu-id="76477-110">Değer</span><span class="sxs-lookup"><span data-stu-id="76477-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="76477-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="76477-111">Scope</span></span>   |<span data-ttu-id="76477-112">Edge</span><span class="sxs-lookup"><span data-stu-id="76477-112">Edge</span></span>|
|<span data-ttu-id="76477-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="76477-113">Version</span></span>|<span data-ttu-id="76477-114">4,5</span><span class="sxs-lookup"><span data-stu-id="76477-114">4.5</span></span>|
|<span data-ttu-id="76477-115">Tür</span><span class="sxs-lookup"><span data-stu-id="76477-115">Type</span></span>|<span data-ttu-id="76477-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="76477-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="76477-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="76477-117">Affected APIs</span></span>

<span data-ttu-id="76477-118">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="76477-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
