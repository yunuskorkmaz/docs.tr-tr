---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620676"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="7714b-101">WF deyimleri seri hale getirir. sabit değerli &lt; T &gt; DateTimeS Now (özel xaml ayrıştırıcılarını keser)</span><span class="sxs-lookup"><span data-stu-id="7714b-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="7714b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7714b-102">Details</span></span>

<span data-ttu-id="7714b-103">İlişkili <xref:System.Windows.Markup.ValueSerializer> nesne, <xref:System.DateTime?displayProperty=fullName> <xref:System.DateTimeOffset?displayProperty=fullName> ikinci ve bileşenleri sıfır olmayan bir veya nesnesi <xref:System.DateTime.Millisecond?displayProperty=fullName> (bir değer için), özelliği de <xref:System.DateTime?displayProperty=fullName> <xref:System.DateTime.Kind> bir dize yerine özellik öğesi söz dizimine belirtilmemiş olarak dönüştürecek.</span><span class="sxs-lookup"><span data-stu-id="7714b-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="7714b-104">Bu değişiklik <xref:System.DateTime?displayProperty=fullName> , ve <xref:System.DateTimeOffset?displayProperty=fullName> değerlerinin yuvarlak olarak değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7714b-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="7714b-105">Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="7714b-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7714b-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="7714b-106">Suggestion</span></span>

<span data-ttu-id="7714b-107">Bu değişiklik <xref:System.DateTime?displayProperty=fullName> , ve <xref:System.DateTimeOffset?displayProperty=fullName> değerlerinin yuvarlak olarak değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7714b-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="7714b-108">Nitelik söz dizimindeki giriş XAML'inin doğru çalışmayacağını varsayan özel XAML ayrıştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="7714b-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="7714b-109">Name</span><span class="sxs-lookup"><span data-stu-id="7714b-109">Name</span></span>    | <span data-ttu-id="7714b-110">Değer</span><span class="sxs-lookup"><span data-stu-id="7714b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7714b-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7714b-111">Scope</span></span>   |<span data-ttu-id="7714b-112">Edge</span><span class="sxs-lookup"><span data-stu-id="7714b-112">Edge</span></span>|
|<span data-ttu-id="7714b-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7714b-113">Version</span></span>|<span data-ttu-id="7714b-114">4,5</span><span class="sxs-lookup"><span data-stu-id="7714b-114">4.5</span></span>|
|<span data-ttu-id="7714b-115">Tür</span><span class="sxs-lookup"><span data-stu-id="7714b-115">Type</span></span>|<span data-ttu-id="7714b-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7714b-116">Runtime</span></span>|
