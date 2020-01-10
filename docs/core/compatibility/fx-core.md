---
title: Son değişiklikler-.NET Core 'a .NET Framework
description: .NET Framework 'den .NET Core 'a yapılan son değişiklikleri listeler.
ms.date: 12/18/2019
ms.openlocfilehash: e01ca522b7ec29e2f6db8a5a0c2fcdfc30a38168
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740907"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="3fd20-103">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="3fd20-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="3fd20-104">.NET Framework bir uygulamayı .NET Core 'a geçiriyorsanız, bu makalede listelenen son değişiklikler sizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="3fd20-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="3fd20-105">Ayrıca, [.NET Core makalesinde kullanılamayan .NET Framework teknolojileri](../porting/net-framework-tech-unavailable.md) .NET Core üzerinde desteklenmeyen teknolojiler (örneğin, uygulama etki alanları ve .NET Remoting) hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fd20-105">In addition, the [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md) article provides information about technologies that aren't supported on .NET Core, for example, application domains and .NET remoting.</span></span>

<span data-ttu-id="3fd20-106">Son değişiklikler kategoriye göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="3fd20-106">Breaking changes are grouped by category.</span></span>

> [!NOTE]
> <span data-ttu-id="3fd20-107">Bu makale, .NET Framework ve .NET Core arasındaki önemli değişikliklerden oluşan bir liste değildir.</span><span class="sxs-lookup"><span data-stu-id="3fd20-107">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="3fd20-108">Bunlara göz önünde bulundurulduğumuz için en önemli son değişiklikler buraya eklenir.</span><span class="sxs-lookup"><span data-stu-id="3fd20-108">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="3fd20-109">CoreFx</span><span class="sxs-lookup"><span data-stu-id="3fd20-109">CoreFx</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a><span data-ttu-id="3fd20-110">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3fd20-110">Windows Forms</span></span>

<span data-ttu-id="3fd20-111">Windows Forms uygulamayı .NET Framework .NET Core 3,0 veya sonraki bir sürüme geçirdiğinizde oluşan değişiklikler hakkında daha fazla bilgi için, bkz. [Windows Forms 'Deki son değişiklikler (.NET Core 'a .NET Framework)](../porting/winforms-breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="3fd20-111">For information about breaking changes when you migrate a Windows Forms app from .NET Framework to .NET Core 3.0 or later, see [Breaking changes in Windows Forms (.NET Framework to .NET Core)](../porting/winforms-breaking-changes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3fd20-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fd20-112">See also</span></span>

- [<span data-ttu-id="3fd20-113">.NET Core 'da .NET Framework teknolojileri kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="3fd20-113">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
