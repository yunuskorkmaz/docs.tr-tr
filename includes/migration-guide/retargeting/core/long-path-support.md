---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614714"
---
### <a name="long-path-support"></a><span data-ttu-id="581b2-101">Uzun yol desteği</span><span class="sxs-lookup"><span data-stu-id="581b2-101">Long path support</span></span>

#### <a name="details"></a><span data-ttu-id="581b2-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="581b2-102">Details</span></span>

<span data-ttu-id="581b2-103">.NET Framework 4.6.2 hedeflenen uygulamalardan başlayarak, uzun yollar (en fazla 32K karakter) desteklenir ve yol uzunlukları 260 karakterlik (veya `MAX_PATH` ) sınırlaması kaldırılmıştır. .NET Framework 4.6.2 hedeflemek üzere yeniden derlenen uygulamalar için, bir yol 260 karakteri aştığından daha önce bir olan kod yolları <xref:System.IO.PathTooLongException?displayProperty=fullName> Şimdi <xref:System.IO.PathTooLongException?displayProperty=fullName> yalnızca aşağıdaki koşullarda bir oluşturacak:</span><span class="sxs-lookup"><span data-stu-id="581b2-103">Starting with apps that target the .NET Framework 4.6.2, long paths (of up to 32K characters) are supported, and the 260-character (or `MAX_PATH`) limitation on path lengths has been removed.For apps that are recompiled to target the .NET Framework 4.6.2, code paths that previously threw a <xref:System.IO.PathTooLongException?displayProperty=fullName> because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException?displayProperty=fullName> only under the following conditions:</span></span>

- <span data-ttu-id="581b2-104">Yolun uzunluğu <xref:System.Int16.MaxValue> (32.767) karakterden fazla.</span><span class="sxs-lookup"><span data-stu-id="581b2-104">The length of the path is greater than <xref:System.Int16.MaxValue> (32,767) characters.</span></span>
- <span data-ttu-id="581b2-105">İşletim sistemi, `COR_E_PATHTOOLONG` eşdeğerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="581b2-105">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>
<span data-ttu-id="581b2-106">.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen uygulamalar için, bir <xref:System.IO.PathTooLongException?displayProperty=fullName> yol 260 karakteri aştığında çalışma zamanı otomatik olarak bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="581b2-106">For apps that target the .NET Framework 4.6.1 and earlier versions, the runtime automatically throws a <xref:System.IO.PathTooLongException?displayProperty=fullName> whenever a path exceeds 260 characters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="581b2-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="581b2-107">Suggestion</span></span>

<span data-ttu-id="581b2-108">.NET Framework 4.6.2 hedefleyen uygulamalar için, dosyanızın bölümüne aşağıdakiler eklenerek uzun yol desteğini devre dışı bırakabilirsiniz `<runtime>` `app.config` :</span><span class="sxs-lookup"><span data-stu-id="581b2-108">For apps that target the .NET Framework 4.6.2, you can opt out of long path support if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

<span data-ttu-id="581b2-109">.NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.2 veya sonraki sürümlerde çalışan uygulamalar için, dosyanızın bölümüne aşağıdakileri ekleyerek uzun yol desteğini tercih edebilirsiniz `<runtime>` `app.config` :</span><span class="sxs-lookup"><span data-stu-id="581b2-109">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.6.2 or later, you can opt in to long path support by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| <span data-ttu-id="581b2-110">Name</span><span class="sxs-lookup"><span data-stu-id="581b2-110">Name</span></span>    | <span data-ttu-id="581b2-111">Değer</span><span class="sxs-lookup"><span data-stu-id="581b2-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="581b2-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="581b2-112">Scope</span></span>   | <span data-ttu-id="581b2-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="581b2-113">Minor</span></span>       |
| <span data-ttu-id="581b2-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="581b2-114">Version</span></span> | <span data-ttu-id="581b2-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="581b2-115">4.6.2</span></span>       |
| <span data-ttu-id="581b2-116">Tür</span><span class="sxs-lookup"><span data-stu-id="581b2-116">Type</span></span>    | <span data-ttu-id="581b2-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="581b2-117">Retargeting</span></span> |
