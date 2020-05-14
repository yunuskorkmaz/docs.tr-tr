---
title: ICorDebugValue::GetAddress Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 467ba53f90081f0c3499fb22acab96b5e380a3f4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395838"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="c04d1-102">ICorDebugValue::GetAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="c04d1-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="c04d1-103">Bu "ICorDebugValue" nesnesinin, hata ayıklama sürecinde olan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="c04d1-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c04d1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c04d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c04d1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c04d1-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="c04d1-106">dışı `CORDB_ADDRESS`Bu değer nesnesinin adresini belirten nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c04d1-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c04d1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c04d1-107">Remarks</span></span>  
 <span data-ttu-id="c04d1-108">Değer kullanılamıyorsa 0 (sıfır) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c04d1-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="c04d1-109">Bu durum, değer en az kısmen Yazmaçlarda veya çöp toplayıcı tanıtıcısında () depolanıyorsa meydana gelebilir `GCHandle` .</span><span class="sxs-lookup"><span data-stu-id="c04d1-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c04d1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c04d1-110">Requirements</span></span>  
 <span data-ttu-id="c04d1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c04d1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c04d1-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c04d1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c04d1-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c04d1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c04d1-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c04d1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04d1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c04d1-115">See also</span></span>
