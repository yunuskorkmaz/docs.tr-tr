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
ms.openlocfilehash: 3c2bc771c0a131329b9403c99a33ca7b79023771
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420857"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="f186f-102">IXCLRDataModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f186f-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="f186f-103">Yüklü bir modülle ilgili bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f186f-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="f186f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f186f-104">Methods</span></span>

| <span data-ttu-id="f186f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f186f-105">Method</span></span>                                                                                                                                | <span data-ttu-id="f186f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f186f-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="f186f-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="f186f-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="f186f-108">Belirtilen meta veri belirtecine karşılık gelen yöntem tanımını alır.</span><span class="sxs-lookup"><span data-stu-id="f186f-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="f186f-109">İstek</span><span class="sxs-lookup"><span data-stu-id="f186f-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="f186f-110">Modülün verileriyle verilen arabelleği doldurma istekleri.</span><span class="sxs-lookup"><span data-stu-id="f186f-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="f186f-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="f186f-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="f186f-112">Modülün sürüm KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="f186f-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="f186f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f186f-113">Remarks</span></span>

<span data-ttu-id="f186f-114">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="f186f-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="f186f-115">Ancak, `IUnknown` `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="f186f-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="f186f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f186f-116">Requirements</span></span>

<span data-ttu-id="f186f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f186f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f186f-118">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="f186f-118">**Header:** None</span></span>  
<span data-ttu-id="f186f-119">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="f186f-119">**Library:** None</span></span>  
<span data-ttu-id="f186f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f186f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f186f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f186f-121">See also</span></span>

- [<span data-ttu-id="f186f-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f186f-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="f186f-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f186f-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
