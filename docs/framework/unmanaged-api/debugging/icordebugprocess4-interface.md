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
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948815"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="a7ee6-102">ICorDebugProcess4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7ee6-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="a7ee6-103">İşlem yürütme denetimi dışında için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7ee6-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="a7ee6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a7ee6-104">Methods</span></span>

| <span data-ttu-id="a7ee6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a7ee6-105">Method</span></span>                                                                 | <span data-ttu-id="a7ee6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7ee6-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="a7ee6-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="a7ee6-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="a7ee6-108">Icordebug ardışık düzen işlemi hata ayıklayıcı dışı debugee'nın yürütülmesine devam etmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="a7ee6-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a7ee6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7ee6-109">Remarks</span></span>

<span data-ttu-id="a7ee6-110">Bu arabirim, çalışma zamanı içinde bulunur ve herhangi bir üst bilgiler veya kitaplık dosyaları kullanıma.</span><span class="sxs-lookup"><span data-stu-id="a7ee6-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="a7ee6-111">Ancak, bu, türetilen bir COM arabirimidir `IUnknown` GUID'e sahip `E930C679-78AF-4953-8AB7-B0AABF0F9F80` normal COM mekanizmalar aracılığıyla edinilebilir.</span><span class="sxs-lookup"><span data-stu-id="a7ee6-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7ee6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7ee6-112">Requirements</span></span>

<span data-ttu-id="a7ee6-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ee6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a7ee6-114">**Üst bilgi:** Yok.</span><span class="sxs-lookup"><span data-stu-id="a7ee6-114">**Header:** None</span></span>

<span data-ttu-id="a7ee6-115">**Kitaplığı:** None</span><span class="sxs-lookup"><span data-stu-id="a7ee6-115">**Library:** None</span></span>

<span data-ttu-id="a7ee6-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ee6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a7ee6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7ee6-117">See also</span></span>

- [<span data-ttu-id="a7ee6-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7ee6-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a7ee6-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a7ee6-119">Debugging</span></span>](index.md)
