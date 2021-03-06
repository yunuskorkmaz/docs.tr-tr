---
title: 'Son değişiklik: tek dosya yayımlama biçimi için derlemeden ilgili API davranışı değişiklikleri'
description: Bir derlemenin dosya konumuyla ilgili birden çok API 'nin, tek dosya yayımlama biçiminde çağrıldığında davranış değişikliklerinin olduğu çekirdek .NET kitaplıklarında .NET 5 ' in son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 3810a71fac481a42ccf2c8e64149d171f31c6821
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257693"
---
# <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="6d8d1-103">Tek dosya yayımlama biçimi için derlemeden ilgili API davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="6d8d1-103">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="6d8d1-104">Bir derlemenin dosya konumuyla ilgili birden çok API, tek dosya yayımlama biçiminde çağrıldığında davranış değişikliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6d8d1-104">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

## <a name="change-description"></a><span data-ttu-id="6d8d1-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="6d8d1-105">Change description</span></span>

<span data-ttu-id="6d8d1-106">.NET 5 ve sonraki sürümler için tek dosya yayımlama sürümünde, paketlenmiş derlemeler diske ayıklanmak yerine bellekten yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6d8d1-106">In single-file publishing for .NET 5 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="6d8d1-107">Tek dosya yayımlanan uygulamalar için bu, konumla ilgili bazı API 'Lerin .NET 5 ve sonraki sürümlerini önceki .NET sürümlerinden farklı şekilde döndürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6d8d1-107">For single-file published apps, this means that certain location-related APIs return different values on .NET 5 and later than on previous versions of .NET.</span></span> <span data-ttu-id="6d8d1-108">Değişiklikler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6d8d1-108">The changes are as follows:</span></span>

| <span data-ttu-id="6d8d1-109">API</span><span class="sxs-lookup"><span data-stu-id="6d8d1-109">API</span></span> | <span data-ttu-id="6d8d1-110">Önceki sürümler</span><span class="sxs-lookup"><span data-stu-id="6d8d1-110">Previous versions</span></span> | <span data-ttu-id="6d8d1-111">.NET 5 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="6d8d1-111">.NET 5 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="6d8d1-112">Ayıklanan DLL dosyası yolunu döndürür</span><span class="sxs-lookup"><span data-stu-id="6d8d1-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="6d8d1-113">Paketlenmiş derlemeler için boş dize döndürür</span><span class="sxs-lookup"><span data-stu-id="6d8d1-113">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="6d8d1-114">Ayıklanan DLL dosyası yolunu döndürür</span><span class="sxs-lookup"><span data-stu-id="6d8d1-114">Returns extracted DLL file path</span></span> | <span data-ttu-id="6d8d1-115">Paketlenmiş derlemeler için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="6d8d1-115">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="6d8d1-116">`null`Paketlenmiş derlemeler için döndürür</span><span class="sxs-lookup"><span data-stu-id="6d8d1-116">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="6d8d1-117">Paketlenmiş derlemeler için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="6d8d1-117">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="6d8d1-118">Değer, giriş noktası DLL 'inin adıdır</span><span class="sxs-lookup"><span data-stu-id="6d8d1-118">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="6d8d1-119">Değer, ana bilgisayarın yürütülebilir dosyasının adıdır</span><span class="sxs-lookup"><span data-stu-id="6d8d1-119">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="6d8d1-120">Değer, geçici ayıklama dizinidir</span><span class="sxs-lookup"><span data-stu-id="6d8d1-120">Value is the temporary extraction directory</span></span> | <span data-ttu-id="6d8d1-121">Değer, ana bilgisayarın yürütülebilir dosyasının bulunduğu dizin</span><span class="sxs-lookup"><span data-stu-id="6d8d1-121">Value is the containing directory of the host executable</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="6d8d1-122">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6d8d1-122">Version introduced</span></span>

<span data-ttu-id="6d8d1-123">5.0</span><span class="sxs-lookup"><span data-stu-id="6d8d1-123">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6d8d1-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6d8d1-124">Recommended action</span></span>

<span data-ttu-id="6d8d1-125">Tek bir dosya olarak yayımlarken derlemelerin dosya konumundaki bağımlılıklardan kaçının.</span><span class="sxs-lookup"><span data-stu-id="6d8d1-125">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6d8d1-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6d8d1-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
