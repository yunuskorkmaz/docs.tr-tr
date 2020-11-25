---
title: ICorDebugAppDomainEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: 37b6bcb48681704e3db47f81a51a9d21f00dfb37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723200"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="488e6-102">ICorDebugAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="488e6-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="488e6-103">, `Next` `ICorDebugAppDomainEnum` Numaralandırmadaki bir sonraki konumdan başlayarak belirtilen sayıda değer döndüren yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="488e6-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="488e6-104">Bu arabirim "ıcordebuggenum" öğesinin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="488e6-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="488e6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="488e6-105">Methods</span></span>  
  
|<span data-ttu-id="488e6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="488e6-106">Method</span></span>|<span data-ttu-id="488e6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="488e6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="488e6-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="488e6-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="488e6-109">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda uygulama etki alanı alır.</span><span class="sxs-lookup"><span data-stu-id="488e6-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="488e6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="488e6-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="488e6-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="488e6-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="488e6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="488e6-112">Requirements</span></span>  

 <span data-ttu-id="488e6-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="488e6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="488e6-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="488e6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="488e6-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="488e6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="488e6-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="488e6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488e6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="488e6-117">See also</span></span>

- [<span data-ttu-id="488e6-118">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="488e6-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="488e6-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="488e6-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
