---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981647"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="02a21-101">COR_PRF_GC_ROOT_HANDLEs profil oluşturucular tarafından numaralandırılan değil</span><span class="sxs-lookup"><span data-stu-id="02a21-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="02a21-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="02a21-102">Details</span></span>|<span data-ttu-id="02a21-103">.NET Framework v4.5.1, profil oluşturma API içinde <code>RootReferences2()</code> yanlış hiçbir zaman döndüren <code>COR_PRF_GC_ROOT_HANDLE</code> (olarak döndürülen <code>COR_PRF_GC_ROOT_OTHER</code> bunun yerine).</span><span class="sxs-lookup"><span data-stu-id="02a21-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="02a21-104">.NET Framework 4. 6 ' ' den itibaren bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="02a21-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="02a21-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="02a21-105">Suggestion</span></span>|<span data-ttu-id="02a21-106">Bu sorun, .NET Framework 4. 6 ' sabit ve .NET Framework'ün bu sürümüne yükseltme tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="02a21-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="02a21-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="02a21-107">Scope</span></span>|<span data-ttu-id="02a21-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="02a21-108">Minor</span></span>|
|<span data-ttu-id="02a21-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="02a21-109">Version</span></span>|<span data-ttu-id="02a21-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="02a21-110">4.5.1</span></span>|
|<span data-ttu-id="02a21-111">Tür</span><span class="sxs-lookup"><span data-stu-id="02a21-111">Type</span></span>|<span data-ttu-id="02a21-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="02a21-112">Runtime</span></span>|
