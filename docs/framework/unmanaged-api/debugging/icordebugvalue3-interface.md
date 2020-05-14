---
title: ICorDebugValue3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 9f521eb942f37b8cf1d00bcc672071a69692b876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396644"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="819ea-102">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="819ea-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="819ea-103">2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="819ea-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="819ea-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="819ea-104">Methods</span></span>  
  
|<span data-ttu-id="819ea-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="819ea-105">Method</span></span>|<span data-ttu-id="819ea-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="819ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="819ea-107">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="819ea-107">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="819ea-108">Bu nesnenin boyutunu bayt cinsinden alır `ICorDebugValue3` .</span><span class="sxs-lookup"><span data-stu-id="819ea-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="819ea-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="819ea-109">Remarks</span></span>  
 <span data-ttu-id="819ea-110">[ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) yöntemi, 0 ile 2.147.483.647 bayt arasında değişen bir nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="819ea-110">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="819ea-111">.NET Framework 4,5 ' de, dizilerin boyutu 2 GB 'ı aşabilirler.</span><span class="sxs-lookup"><span data-stu-id="819ea-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="819ea-112">`ICorDebugValue3`Arabirim, bu dizilerin boyutunu belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="819ea-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="819ea-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="819ea-113">Requirements</span></span>  
 <span data-ttu-id="819ea-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="819ea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="819ea-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="819ea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="819ea-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="819ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="819ea-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="819ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="819ea-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="819ea-118">See also</span></span>

- [<span data-ttu-id="819ea-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="819ea-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="819ea-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="819ea-120">Debugging</span></span>](index.md)
