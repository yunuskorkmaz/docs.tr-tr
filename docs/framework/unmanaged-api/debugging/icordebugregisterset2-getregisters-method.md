---
description: 'Daha fazla bilgi edinin: ICorDebugRegisterSet2:: Getyazmaçları yöntemi'
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
ms.openlocfilehash: 58af939b0e88185e2be23b69ca70d28e93ff873f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794799"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="0588f-103">ICorDebugRegisterSet2:: Getyazmaçları yöntemi</span><span class="sxs-lookup"><span data-stu-id="0588f-103">ICorDebugRegisterSet2::GetRegisters method</span></span>

<span data-ttu-id="0588f-104">Verilen bit maskesi tarafından belirtilen her kaydın değerini alır (kodun Şu anda yürütüldüğü platform için).</span><span class="sxs-lookup"><span data-stu-id="0588f-104">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0588f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0588f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0588f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0588f-106">Parameters</span></span>

 `maskCount`  
 <span data-ttu-id="0588f-107">'ndaki Dizinin bayt cinsinden boyutu `mask` .</span><span class="sxs-lookup"><span data-stu-id="0588f-107">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="0588f-108">'ndaki Her bitin bir kayda karşılık gelen bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="0588f-108">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="0588f-109">Bit 1 ise, karşılık gelen yazmaç değeri alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="0588f-109">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="0588f-110">'ndaki Alınacak kayıt değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="0588f-110">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="0588f-111">dışı `CORDB_REGISTER` Her biri bir yazmaç değerini alan bir nesne dizisi.</span><span class="sxs-lookup"><span data-stu-id="0588f-111">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0588f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0588f-112">Remarks</span></span>

 <span data-ttu-id="0588f-113">`GetRegisters`Yöntemi, maske tarafından belirtilen yazmaçlardan bir değer dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0588f-113">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="0588f-114">Dizi, maske biti ayarlanmamış yazmaçların değerlerini içermiyor.</span><span class="sxs-lookup"><span data-stu-id="0588f-114">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="0588f-115">Bu nedenle, `regBuffer` dizinin boyutu maskenin içindeki 1 sayısına eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0588f-115">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="0588f-116">Değeri, `regCount` maske tarafından belirtilen kayıt sayısı için çok küçükse, daha yüksek numaralandırılmış yazmaçların değerleri kümeden kesilir.</span><span class="sxs-lookup"><span data-stu-id="0588f-116">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="0588f-117">`regCount`Çok büyükse, kullanılmamış `regBuffer` öğeler değiştirilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="0588f-117">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="0588f-118">Maske tarafından kullanılamayan bir kayıt belirtilmişse, bu kayıt için belirsiz bir değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0588f-118">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="0588f-119">`ICorDebugRegisterSet2::GetRegisters`Yöntemi 64 'den fazla kaydı olan platformlar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0588f-119">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms that have more than 64 registers.</span></span> <span data-ttu-id="0588f-120">Örneğin, ıA64 128 genel amaçlı kayıt kayıtları ve 128 kayan nokta kayıtları içerir, bu nedenle bit maskesinde en fazla 64 bit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0588f-120">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64 bits in the bit mask.</span></span>  
  
 <span data-ttu-id="0588f-121">64 ' den fazla kayıt yoksa, x86 gibi platformlarda olduğu gibi, `GetRegisters` yöntemi yalnızca `mask` bayt dizisindeki baytları a 'ya çevirir `ULONG64` ve ardından maskeyi alan [ICorDebugRegisterSet:: getyazmaçları](icordebugregisterset-getregisters-method.md) yöntemini çağırır `ULONG64` .</span><span class="sxs-lookup"><span data-stu-id="0588f-121">If you don't have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0588f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0588f-122">Requirements</span></span>

 <span data-ttu-id="0588f-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0588f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0588f-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0588f-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0588f-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0588f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0588f-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0588f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0588f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0588f-127">See also</span></span>

- [<span data-ttu-id="0588f-128">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0588f-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="0588f-129">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0588f-129">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
