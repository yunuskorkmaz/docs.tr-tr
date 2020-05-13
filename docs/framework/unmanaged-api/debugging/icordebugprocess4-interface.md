---
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
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213588"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="2b63d-102">ICorDebugProcess4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b63d-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="2b63d-103">İşlem dışı yürütme denetimi için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b63d-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="2b63d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2b63d-104">Methods</span></span>

| <span data-ttu-id="2b63d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2b63d-105">Method</span></span>                                                                 | <span data-ttu-id="2b63d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b63d-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="2b63d-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="2b63d-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="2b63d-108">ICorDebug ardışık düzenine, işlem hata ayıklamanın dışına ayıklandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2b63d-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2b63d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b63d-109">Remarks</span></span>

<span data-ttu-id="2b63d-110">Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="2b63d-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="2b63d-111">Ancak, `IUnknown` `E930C679-78AF-4953-8AB7-B0AABF0F9F80` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="2b63d-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b63d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b63d-112">Requirements</span></span>

<span data-ttu-id="2b63d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b63d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2b63d-114">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="2b63d-114">**Header:** None</span></span>

<span data-ttu-id="2b63d-115">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="2b63d-115">**Library:** None</span></span>

<span data-ttu-id="2b63d-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b63d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2b63d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b63d-117">See also</span></span>

- [<span data-ttu-id="2b63d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2b63d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2b63d-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2b63d-119">Debugging</span></span>](index.md)
