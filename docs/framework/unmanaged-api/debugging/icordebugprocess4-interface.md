---
description: 'Daha fazla bilgi edinin: ICorDebugProcess4 Interface'
title: ICorDebugProcess4 Arabirimi
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 16c7f3fbd1a79b1406fe0c19a9d922964667a2a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650007"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="768a0-103">ICorDebugProcess4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="768a0-103">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="768a0-104">İşlem dışı yürütme denetimi için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="768a0-104">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="768a0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="768a0-105">Methods</span></span>

| <span data-ttu-id="768a0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="768a0-106">Method</span></span>                                                                 | <span data-ttu-id="768a0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="768a0-107">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="768a0-108">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="768a0-108">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="768a0-109">ICorDebug ardışık düzenine, işlem hata ayıklamanın dışına ayıklandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="768a0-109">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="768a0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="768a0-110">Remarks</span></span>

<span data-ttu-id="768a0-111">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="768a0-111">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="768a0-112">Ancak, `IUnknown` `E930C679-78AF-4953-8AB7-B0AABF0F9F80` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="768a0-112">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="768a0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="768a0-113">Requirements</span></span>

<span data-ttu-id="768a0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="768a0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="768a0-115">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="768a0-115">**Header:** None</span></span>

<span data-ttu-id="768a0-116">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="768a0-116">**Library:** None</span></span>

<span data-ttu-id="768a0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="768a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="768a0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="768a0-118">See also</span></span>

- [<span data-ttu-id="768a0-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="768a0-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="768a0-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="768a0-120">Debugging</span></span>](index.md)
