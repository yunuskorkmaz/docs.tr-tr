---
title: ICorDebugRegisterSet::GetRegisters Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178540"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="3e838-102">ICorDebugRegisterSet::GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="3e838-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="3e838-103">Bit maskesi tarafından belirtilen her kaydın (şu anda kodu yürüten bilgisayarda) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="3e838-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e838-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e838-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e838-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e838-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="3e838-106">[içinde] Hangi kayıt değerlerinin alıneceğini belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="3e838-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="3e838-107">Her bit bir kayda karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3e838-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="3e838-108">Bir bit bire ayarlanırsa, kaydın değeri alınır; aksi takdirde, kaydın değeri alınmaz.</span><span class="sxs-lookup"><span data-stu-id="3e838-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="3e838-109">[içinde] Alınacak kayıt değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="3e838-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="3e838-110">[çıkış] Her biri `CORDB_REGISTER` bir kayıt değeri alan bir nesne dizisi.</span><span class="sxs-lookup"><span data-stu-id="3e838-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e838-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e838-111">Remarks</span></span>  
 <span data-ttu-id="3e838-112">Dizinin boyutu bit maskesinde bire ayarlanmış bit sayısına eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e838-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="3e838-113">Parametre, `regCount` arabellekte kayıt değerlerini alacak öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e838-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="3e838-114">`regCount` Değer maske tarafından belirtilen kayıt sayısı için çok küçükse, daha yüksek numaralanmış kayıtlar kümeden kesilir.</span><span class="sxs-lookup"><span data-stu-id="3e838-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="3e838-115">Değer `regCount` çok büyükse, kullanılmayan `regBuffer` öğeler değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="3e838-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="3e838-116">Bit maskesi kullanılamayan bir kayıt belirtirse, `GetRegisters` bu kayıt için belirsiz bir değer verir.</span><span class="sxs-lookup"><span data-stu-id="3e838-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e838-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e838-117">Requirements</span></span>  
 <span data-ttu-id="3e838-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e838-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e838-119">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e838-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e838-120">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e838-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e838-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e838-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e838-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e838-122">See also</span></span>

- [<span data-ttu-id="3e838-123">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e838-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="3e838-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e838-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
