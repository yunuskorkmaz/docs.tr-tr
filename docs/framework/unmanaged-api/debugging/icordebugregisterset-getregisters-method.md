---
description: ': ICorDebugRegisterSet:: Getyazmaçları yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: efb0f19fe9eb823912203b82267803739fc3e2cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690853"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="21a24-103">ICorDebugRegisterSet::GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="21a24-103">ICorDebugRegisterSet::GetRegisters Method</span></span>

<span data-ttu-id="21a24-104">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="21a24-104">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a24-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21a24-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21a24-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21a24-106">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="21a24-107">'ndaki Hangi yazmaç değerlerinin alınacağını belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="21a24-107">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="21a24-108">Her bit bir kayda karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="21a24-108">Each bit corresponds to a register.</span></span> <span data-ttu-id="21a24-109">Bir bit olarak ayarlandıysa, kaydın değeri alınır; Aksi takdirde, kaydın değeri alınmadı.</span><span class="sxs-lookup"><span data-stu-id="21a24-109">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="21a24-110">'ndaki Alınacak kayıt değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="21a24-110">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="21a24-111">dışı `CORDB_REGISTER` Her biri bir yazmaç değeri alan bir nesne dizisi.</span><span class="sxs-lookup"><span data-stu-id="21a24-111">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21a24-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21a24-112">Remarks</span></span>  

 <span data-ttu-id="21a24-113">Dizinin boyutu, bit maskesinde bir tane olarak ayarlanan bit sayısına eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21a24-113">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="21a24-114">`regCount`Parametresi, kayıt değerlerini alacak arabellekteki öğelerin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21a24-114">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="21a24-115">Değer, `regCount` maskenin gösterdiği kayıt sayısı için çok küçük ise, üstteki numaralandırılmış Yazmaçları kümeden kesilecek.</span><span class="sxs-lookup"><span data-stu-id="21a24-115">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="21a24-116">`regCount`Değer çok büyükse, kullanılmamış `regBuffer` öğeler değiştirilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="21a24-116">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="21a24-117">Bit maskesi kullanılamayan bir kaydı belirtirse, `GetRegisters` Bu kayıt için belirsiz bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="21a24-117">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a24-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21a24-118">Requirements</span></span>  

 <span data-ttu-id="21a24-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21a24-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a24-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="21a24-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21a24-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21a24-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21a24-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21a24-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a24-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21a24-123">See also</span></span>

- [<span data-ttu-id="21a24-124">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21a24-124">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="21a24-125">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21a24-125">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
