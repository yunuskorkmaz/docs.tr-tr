---
title: '.NET 6 Son değişiklik: LINQ Queryable yöntemlerinin ek aşırı yüklemeleri'
description: System. Linq. Queryable türüne ek yöntem aşırı yüklemelerinin eklendiği çekirdek .NET kitaplıklarında .NET 6 ' dan fazla değişiklik hakkında bilgi edinin.
ms.date: 03/31/2021
ms.openlocfilehash: 15a4e480f7d1b4e110084e736fc920a522439e69
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106123578"
---
# <a name="new-systemlinqqueryable-method-overloads"></a><span data-ttu-id="4ae46-103">Yeni System. LINQ. Queryable yöntemi aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="4ae46-103">New System.Linq.Queryable method overloads</span></span>

<span data-ttu-id="4ae46-104"><xref:System.Linq.Queryable?displayProperty=fullName>' De uygulanan yeni özelliklerin bir parçası olarak ' ye ek ortak yöntem aşırı yüklemeleri eklenmiştir <https://github.com/dotnet/runtime/pull/47231> .</span><span class="sxs-lookup"><span data-stu-id="4ae46-104">Additional public method overloads have been added to <xref:System.Linq.Queryable?displayProperty=fullName> as part of the new features implemented in <https://github.com/dotnet/runtime/pull/47231>.</span></span> <span data-ttu-id="4ae46-105">Yöntemleri ararken yansıma kodunuz yeterince sağlam değilse, bu eklemeler sorgu sağlayıcısı uygulamalarınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="4ae46-105">If your reflection code isn't sufficiently robust when looking up methods, these additions can break your query provider implementations.</span></span>

## <a name="change-description"></a><span data-ttu-id="4ae46-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="4ae46-106">Change description</span></span>

<span data-ttu-id="4ae46-107">.NET 6 ' da, [etkilenen API 'ler](#affected-apis) bölümünde listelenen yöntemlere yeni aşırı yüklemeler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="4ae46-107">In .NET 6, new overloads were added to the methods listed in the [Affected APIs](#affected-apis) section.</span></span> <span data-ttu-id="4ae46-108">Aşağıdaki örnekte gösterildiği gibi yansıma kodu, bu eklemelerin sonucu olarak kesilebilir:</span><span class="sxs-lookup"><span data-stu-id="4ae46-108">Reflection code, such as that shown in the following example, may break as a result of these additions:</span></span>

```csharp
typeof(System.Linq.Queryable)
    .GetMethods(BindingFlags.Public | BindingFlags.Static)
    .Where(m => m.Name == "ElementAt")
    .Single();
```

<span data-ttu-id="4ae46-109">Bu yansıma kodu artık <xref:System.InvalidOperationException> Şuna benzer bir ileti oluşturacak: **sıra birden fazla öğe içeriyor**.</span><span class="sxs-lookup"><span data-stu-id="4ae46-109">This reflection code will now throw an <xref:System.InvalidOperationException> with a message similar to: **Sequence contains more than one element**.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4ae46-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4ae46-110">Version introduced</span></span>

<span data-ttu-id="4ae46-111">6,0 Preview 3 ve Preview 4</span><span class="sxs-lookup"><span data-stu-id="4ae46-111">6.0 Preview 3 and Preview 4</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4ae46-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4ae46-112">Reason for change</span></span>

<span data-ttu-id="4ae46-113">LINQ API 'yi genişletmek için yeni aşırı yüklemeler eklenmiştir `Queryable` .</span><span class="sxs-lookup"><span data-stu-id="4ae46-113">The new overloads were added to extend the LINQ `Queryable` API.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4ae46-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4ae46-114">Recommended action</span></span>

<span data-ttu-id="4ae46-115">Sorgu sağlayıcı kitaplığı yazarsıysanız, yansıma kodunuzun aşırı yük eklemeleri için dayanıklı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4ae46-115">If you're a query-provider library author, ensure that your reflection code is tolerant of method overload additions.</span></span> <span data-ttu-id="4ae46-116">Örneğin, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> yöntemin parametre türlerini açıkça kabul eden bir aşırı yükleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ae46-116">For example, use a <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> overload that explicitly accepts the method's parameter types.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4ae46-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4ae46-117">Affected APIs</span></span>

<span data-ttu-id="4ae46-118">Aşağıdaki genişletme yöntemleri için yeni aşırı yüklemeler eklendi <xref:System.Linq.Queryable> :</span><span class="sxs-lookup"><span data-stu-id="4ae46-118">New overloads were added for the following <xref:System.Linq.Queryable> extension methods:</span></span>

- <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.Zip%2A?displayProperty=fullName>

<!--

### Category

- Core .NET libraries
- LINQ

### Affected APIs

- `Overload:System.Linq.Queryable.ElementAt`
- `Overload:System.Linq.Queryable.ElementAtOrDefault`
- `Overload:System.Linq.Queryable.Take`
- `Overload:System.Linq.Queryable.Min`
- `Overload:System.Linq.Queryable.Max`
- `Overload:System.Linq.Queryable.FirstOrDefault`
- `Overload:System.Linq.Queryable.LastOrDefault`
- `Overload:System.Linq.Queryable.SingleOrDefault`
- `Overload:System.Linq.Queryable.Zip`

-->
