---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614815"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a><span data-ttu-id="85de1-101">MemberDescriptor. Equals için yanlış uygulama</span><span class="sxs-lookup"><span data-stu-id="85de1-101">Incorrect implementation of MemberDescriptor.Equals</span></span>

#### <a name="details"></a><span data-ttu-id="85de1-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="85de1-102">Details</span></span>

<span data-ttu-id="85de1-103">Yöntemin orijinal uygulanması <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> karşılaştırılan nesnelerden iki farklı dize özelliklerini karşılaştırır: Kategori adı ve açıklama dizesi.</span><span class="sxs-lookup"><span data-stu-id="85de1-103">The original implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method compares two different string properties from the objects being compared: the category name and the description string.</span></span> <span data-ttu-id="85de1-104">Bu çözüm, <xref:System.ComponentModel.MemberDescriptor.Category> birinci nesnenin <xref:System.ComponentModel.MemberDescriptor.Category> ikincisini ikinci bir ile ve <xref:System.ComponentModel.MemberDescriptor.Description> <xref:System.ComponentModel.MemberDescriptor.Description> ikincinin birincisini karşılaştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="85de1-104">The fix is to compare the <xref:System.ComponentModel.MemberDescriptor.Category> of the first object to the <xref:System.ComponentModel.MemberDescriptor.Category> of the second one, and the <xref:System.ComponentModel.MemberDescriptor.Description> of the first to the <xref:System.ComponentModel.MemberDescriptor.Description> of the second.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="85de1-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="85de1-105">Suggestion</span></span>

<span data-ttu-id="85de1-106">Uygulamanız <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> bazen tanımlayıcılar eşdeğer olduğunda geri dönmesine bağımlıysa `false` ve .NET Framework 4.6.2 veya üzerini hedefliyorsanız, birkaç seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="85de1-106">If your application depends on <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> sometimes returning `false` when descriptors are equivalent, and you are targeting the .NET Framework 4.6.2 or later, you have several options:</span></span>

- <span data-ttu-id="85de1-107"><xref:System.ComponentModel.MemberDescriptor.Category> <xref:System.ComponentModel.MemberDescriptor.Description> Yöntemini çağırmaya ek olarak ve alanlarını el ile karşılaştırmak için kod değişiklikleri yapın <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85de1-107">Make code changes to compare the <xref:System.ComponentModel.MemberDescriptor.Category> and <xref:System.ComponentModel.MemberDescriptor.Description> fields manually in addition to calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="85de1-108">app.config dosyasına aşağıdaki değeri ekleyerek bu değişikliği geri çevirin:</span><span class="sxs-lookup"><span data-stu-id="85de1-108">Opt out of this change by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

<span data-ttu-id="85de1-109">Uygulamanız .NET Framework 4.6.1 veya daha önceki bir sürümü hedefliyorsa ve .NET Framework 4.6.2 ya da üzerinde çalışıyorsa ve bu değişikliği etkinleştirmek istiyorsanız, `false` app.config dosyasına aşağıdaki değeri ekleyerek uyumluluk anahtarını olarak ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="85de1-109">If your application targets .NET Framework 4.6.1 or earlier and is running on the .NET Framework 4.6.2 or later and you want this change enabled, you can set the compatibility switch to `false` by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| <span data-ttu-id="85de1-110">Name</span><span class="sxs-lookup"><span data-stu-id="85de1-110">Name</span></span>    | <span data-ttu-id="85de1-111">Değer</span><span class="sxs-lookup"><span data-stu-id="85de1-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85de1-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="85de1-112">Scope</span></span>   | <span data-ttu-id="85de1-113">Edge</span><span class="sxs-lookup"><span data-stu-id="85de1-113">Edge</span></span>        |
| <span data-ttu-id="85de1-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="85de1-114">Version</span></span> | <span data-ttu-id="85de1-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="85de1-115">4.6.2</span></span>       |
| <span data-ttu-id="85de1-116">Tür</span><span class="sxs-lookup"><span data-stu-id="85de1-116">Type</span></span>    | <span data-ttu-id="85de1-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="85de1-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="85de1-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="85de1-118">Affected APIs</span></span>

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
