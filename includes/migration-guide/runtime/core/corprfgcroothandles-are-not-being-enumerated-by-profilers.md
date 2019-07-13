---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858573"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="f188e-101">COR_PRF_GC_ROOT_HANDLEs profil oluşturucular tarafından numaralandırılan değil</span><span class="sxs-lookup"><span data-stu-id="f188e-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f188e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f188e-102">Details</span></span>|<span data-ttu-id="f188e-103">.NET Framework v4.5.1, profil oluşturma API içinde <code>RootReferences2()</code> yanlış hiçbir zaman döndüren <code>COR_PRF_GC_ROOT_HANDLE</code> (olarak döndürülen <code>COR_PRF_GC_ROOT_OTHER</code> bunun yerine).</span><span class="sxs-lookup"><span data-stu-id="f188e-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="f188e-104">.NET Framework 4. 6 ' ' den itibaren bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f188e-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="f188e-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="f188e-105">Suggestion</span></span>|<span data-ttu-id="f188e-106">Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f188e-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="f188e-107">`Scope`</span><span class="sxs-lookup"><span data-stu-id="f188e-107">Scope</span></span>|<span data-ttu-id="f188e-108">Küçük</span><span class="sxs-lookup"><span data-stu-id="f188e-108">Minor</span></span>|
|<span data-ttu-id="f188e-109">Version</span><span class="sxs-lookup"><span data-stu-id="f188e-109">Version</span></span>|<span data-ttu-id="f188e-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f188e-110">4.5.1</span></span>|
|<span data-ttu-id="f188e-111">Type</span><span class="sxs-lookup"><span data-stu-id="f188e-111">Type</span></span>|<span data-ttu-id="f188e-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="f188e-112">Runtime</span></span>|

