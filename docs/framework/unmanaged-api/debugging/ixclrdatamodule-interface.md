---
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
ms.openlocfilehash: 8757642db6c4375cf55d1f7288669c4c8a752a38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790402"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="67e4a-102">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67e4a-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="67e4a-103">Yüklü bir modülle ilgili bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="67e4a-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="67e4a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="67e4a-104">Methods</span></span>

| <span data-ttu-id="67e4a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="67e4a-105">Method</span></span>                                                                                                                                | <span data-ttu-id="67e4a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67e4a-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="67e4a-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="67e4a-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="67e4a-108">Belirtilen meta veri belirtecine karşılık gelen yöntem tanımını alır.</span><span class="sxs-lookup"><span data-stu-id="67e4a-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="67e4a-109">İstek</span><span class="sxs-lookup"><span data-stu-id="67e4a-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="67e4a-110">Modülün verileriyle verilen arabelleği doldurma istekleri.</span><span class="sxs-lookup"><span data-stu-id="67e4a-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="67e4a-111">Getversionıd</span><span class="sxs-lookup"><span data-stu-id="67e4a-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="67e4a-112">Modülün sürüm KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="67e4a-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="67e4a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67e4a-113">Remarks</span></span>

<span data-ttu-id="67e4a-114">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="67e4a-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="67e4a-115">Ancak, normal COM mekanizmalarından elde edilebilir GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` `IUnknown` türetilen bir COM arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="67e4a-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="67e4a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67e4a-116">Requirements</span></span>

<span data-ttu-id="67e4a-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67e4a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="67e4a-118">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="67e4a-118">**Header:** None</span></span>  
<span data-ttu-id="67e4a-119">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="67e4a-119">**Library:** None</span></span>  
<span data-ttu-id="67e4a-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="67e4a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="67e4a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e4a-121">See also</span></span>

- [<span data-ttu-id="67e4a-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="67e4a-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="67e4a-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="67e4a-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
