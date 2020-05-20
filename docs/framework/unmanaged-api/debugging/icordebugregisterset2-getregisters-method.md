---
title: ICorDebugRegisterSet2::GetRegisters Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
ms.openlocfilehash: 71b9d59621efb547713cb4a6c9df7a7142f4a677
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615195"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="28cb4-102">ICorDebugRegisterSet2:: Getyazmaçları yöntemi</span><span class="sxs-lookup"><span data-stu-id="28cb4-102">ICorDebugRegisterSet2::GetRegisters method</span></span>

<span data-ttu-id="28cb4-103">Verilen bit maskesi tarafından belirtilen her kaydın değerini alır (kodun Şu anda yürütüldüğü platform için).</span><span class="sxs-lookup"><span data-stu-id="28cb4-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28cb4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="28cb4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28cb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28cb4-105">Parameters</span></span>

 `maskCount`  
 <span data-ttu-id="28cb4-106">'ndaki Dizinin bayt cinsinden boyutu `mask` .</span><span class="sxs-lookup"><span data-stu-id="28cb4-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="28cb4-107">'ndaki Her bitin bir kayda karşılık gelen bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="28cb4-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="28cb4-108">Bit 1 ise, karşılık gelen yazmaç değeri alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="28cb4-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="28cb4-109">'ndaki Alınacak kayıt değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="28cb4-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="28cb4-110">dışı `CORDB_REGISTER`Her biri bir yazmaç değerini alan bir nesne dizisi.</span><span class="sxs-lookup"><span data-stu-id="28cb4-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28cb4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28cb4-111">Remarks</span></span>

 <span data-ttu-id="28cb4-112">`GetRegisters`Yöntemi, maske tarafından belirtilen yazmaçlardan bir değer dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="28cb4-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="28cb4-113">Dizi, maske biti ayarlanmamış yazmaçların değerlerini içermiyor.</span><span class="sxs-lookup"><span data-stu-id="28cb4-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="28cb4-114">Bu nedenle, `regBuffer` dizinin boyutu maskenin içindeki 1 sayısına eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28cb4-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="28cb4-115">Değeri, `regCount` maske tarafından belirtilen kayıt sayısı için çok küçükse, daha yüksek numaralandırılmış yazmaçların değerleri kümeden kesilir.</span><span class="sxs-lookup"><span data-stu-id="28cb4-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="28cb4-116">`regCount`Çok büyükse, kullanılmamış `regBuffer` öğeler değiştirilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="28cb4-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="28cb4-117">Maske tarafından kullanılamayan bir kayıt belirtilmişse, bu kayıt için belirsiz bir değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="28cb4-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="28cb4-118">`ICorDebugRegisterSet2::GetRegisters`Yöntemi 64 'den fazla kaydı olan platformlar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="28cb4-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms that have more than 64 registers.</span></span> <span data-ttu-id="28cb4-119">Örneğin, ıA64 128 genel amaçlı kayıt kayıtları ve 128 kayan nokta kayıtları içerir, bu nedenle bit maskesinde en fazla 64 bit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28cb4-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64 bits in the bit mask.</span></span>  
  
 <span data-ttu-id="28cb4-120">64 ' den fazla kayıt yoksa, x86 gibi platformlarda olduğu gibi, `GetRegisters` yöntemi yalnızca `mask` bayt dizisindeki baytları a 'ya çevirir `ULONG64` ve ardından maskeyi alan [ICorDebugRegisterSet:: getyazmaçları](icordebugregisterset-getregisters-method.md) yöntemini çağırır `ULONG64` .</span><span class="sxs-lookup"><span data-stu-id="28cb4-120">If you don't have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28cb4-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28cb4-121">Requirements</span></span>

 <span data-ttu-id="28cb4-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28cb4-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28cb4-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="28cb4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28cb4-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="28cb4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28cb4-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28cb4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28cb4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28cb4-126">See also</span></span>

- [<span data-ttu-id="28cb4-127">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28cb4-127">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="28cb4-128">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28cb4-128">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
