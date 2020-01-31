---
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
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790474"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="d5b1c-102">ISOSDacInterface Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5b1c-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="d5b1c-103">`SOS`verilere erişmek için yardımcı yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5b1c-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="d5b1c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d5b1c-104">Methods</span></span>

| <span data-ttu-id="d5b1c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d5b1c-105">Method</span></span>                                                                                                               | <span data-ttu-id="d5b1c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5b1c-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="d5b1c-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="d5b1c-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="d5b1c-108">Verilen MethodDesc işaretçisi için verileri alır.</span><span class="sxs-lookup"><span data-stu-id="d5b1c-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="d5b1c-109">Getmethoddescptrfromıp</span><span class="sxs-lookup"><span data-stu-id="d5b1c-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="d5b1c-110">Verilen yerel yönerge adresini içeren yöntemi karşılık gelen MethodDesc işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="d5b1c-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="d5b1c-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="d5b1c-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="d5b1c-112">Verilen bir adreste yüklü olan modüle karşılık gelen verileri getirir.</span><span class="sxs-lookup"><span data-stu-id="d5b1c-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d5b1c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5b1c-113">Remarks</span></span>

<span data-ttu-id="d5b1c-114">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="d5b1c-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="d5b1c-115">Ancak, normal COM mekanizmalarından elde edilebilir GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` `IUnknown` türetilen bir COM arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="d5b1c-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5b1c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5b1c-116">Requirements</span></span>

<span data-ttu-id="d5b1c-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5b1c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d5b1c-118">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="d5b1c-118">**Header:** None</span></span>  
<span data-ttu-id="d5b1c-119">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="d5b1c-119">**Library:** None</span></span>  
<span data-ttu-id="d5b1c-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b1c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d5b1c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5b1c-121">See also</span></span>

- [<span data-ttu-id="d5b1c-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d5b1c-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="d5b1c-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5b1c-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
