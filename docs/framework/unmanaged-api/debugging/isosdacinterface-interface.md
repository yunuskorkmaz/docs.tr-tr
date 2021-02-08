---
description: 'Daha fazla bilgi edinin: Isosdacınterface arabirimi'
title: ISOSDacInterface Arabirimi
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ddb99b7c6fca6870024f04933861d01e4b31ea9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790405"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="ee309-103">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee309-103">ISOSDacInterface Interface</span></span>

<span data-ttu-id="ee309-104">Verilerine erişmek için yardımcı yöntemler sağlar `SOS` .</span><span class="sxs-lookup"><span data-stu-id="ee309-104">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ee309-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ee309-105">Methods</span></span>

| <span data-ttu-id="ee309-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ee309-106">Method</span></span>                                                                                                               | <span data-ttu-id="ee309-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee309-107">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ee309-108">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="ee309-108">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="ee309-109">Verilen MethodDesc işaretçisi için verileri alır.</span><span class="sxs-lookup"><span data-stu-id="ee309-109">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="ee309-110">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="ee309-110">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="ee309-111">Verilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="ee309-111">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="ee309-112">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="ee309-112">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="ee309-113">Verilen bir adreste yüklü olan modüle karşılık gelen verileri getirir.</span><span class="sxs-lookup"><span data-stu-id="ee309-113">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ee309-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee309-114">Remarks</span></span>

<span data-ttu-id="ee309-115">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="ee309-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ee309-116">Ancak, `IUnknown` `436f00f2-b42a-4b9f-870c-e73db66ae930` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="ee309-116">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee309-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee309-117">Requirements</span></span>

<span data-ttu-id="ee309-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee309-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ee309-119">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="ee309-119">**Header:** None</span></span>  
<span data-ttu-id="ee309-120">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="ee309-120">**Library:** None</span></span>  
<span data-ttu-id="ee309-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ee309-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ee309-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee309-122">See also</span></span>

- [<span data-ttu-id="ee309-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ee309-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="ee309-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ee309-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
