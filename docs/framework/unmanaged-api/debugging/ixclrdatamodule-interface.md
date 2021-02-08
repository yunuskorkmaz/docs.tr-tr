---
description: 'Daha fazla bilgi edinin: IXCLRDataModule Interface'
title: IXCLRDataModule Arabirimi
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 403d4dd3db64f2855347562da7217a3562985c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800753"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="15a89-103">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15a89-103">IXCLRDataModule Interface</span></span>

<span data-ttu-id="15a89-104">Yüklü bir modülle ilgili bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="15a89-104">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="15a89-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="15a89-105">Methods</span></span>

| <span data-ttu-id="15a89-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="15a89-106">Method</span></span>                                                                                                                                | <span data-ttu-id="15a89-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15a89-107">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="15a89-108">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="15a89-108">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="15a89-109">Belirtilen meta veri belirtecine karşılık gelen yöntem tanımını alır.</span><span class="sxs-lookup"><span data-stu-id="15a89-109">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="15a89-110">İstek</span><span class="sxs-lookup"><span data-stu-id="15a89-110">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="15a89-111">Modülün verileriyle verilen arabelleği doldurma istekleri.</span><span class="sxs-lookup"><span data-stu-id="15a89-111">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="15a89-112">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="15a89-112">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="15a89-113">Modülün sürüm KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="15a89-113">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="15a89-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15a89-114">Remarks</span></span>

<span data-ttu-id="15a89-115">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="15a89-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="15a89-116">Ancak, `IUnknown` `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="15a89-116">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="15a89-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15a89-117">Requirements</span></span>

<span data-ttu-id="15a89-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a89-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="15a89-119">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="15a89-119">**Header:** None</span></span>  
<span data-ttu-id="15a89-120">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="15a89-120">**Library:** None</span></span>  
<span data-ttu-id="15a89-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="15a89-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="15a89-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15a89-122">See also</span></span>

- [<span data-ttu-id="15a89-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="15a89-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="15a89-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15a89-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
