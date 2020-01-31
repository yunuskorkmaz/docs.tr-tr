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
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792113"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="adee5-102">ICorDebugRegisterSet::GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="adee5-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="adee5-103">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="adee5-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adee5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adee5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adee5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="adee5-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="adee5-106">'ndaki Hangi yazmaç değerlerinin alınacağını belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="adee5-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="adee5-107">Her bit bir kayda karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="adee5-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="adee5-108">Bir bit olarak ayarlandıysa, kaydın değeri alınır; Aksi takdirde, kaydın değeri alınmadı.</span><span class="sxs-lookup"><span data-stu-id="adee5-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="adee5-109">'ndaki Alınacak kayıt değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="adee5-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="adee5-110">dışı Her biri bir yazmaç değeri alan `CORDB_REGISTER` nesnelerden oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="adee5-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adee5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="adee5-111">Remarks</span></span>  
 <span data-ttu-id="adee5-112">Dizinin boyutu, bit maskesinde bir tane olarak ayarlanan bit sayısına eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="adee5-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="adee5-113">`regCount` parametresi, kayıt değerlerini alacak arabellekteki öğelerin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="adee5-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="adee5-114">`regCount` değeri maskenin gösterdiği kayıt sayısı için çok küçük ise, daha yüksek numaralandırılmış Yazmaçları kümeden kesilecek.</span><span class="sxs-lookup"><span data-stu-id="adee5-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="adee5-115">`regCount` değeri çok büyükse, kullanılmamış `regBuffer` öğeleri değiştirilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="adee5-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="adee5-116">Bit maskesi kullanılamayan bir kaydı belirtirse `GetRegisters`, bu kayıt için belirsiz bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="adee5-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adee5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="adee5-117">Requirements</span></span>  
 <span data-ttu-id="adee5-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adee5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adee5-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="adee5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adee5-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="adee5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adee5-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adee5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adee5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adee5-122">See also</span></span>

- [<span data-ttu-id="adee5-123">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adee5-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="adee5-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adee5-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
