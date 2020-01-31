---
title: ICorDebugProcess6::DecodeEvent Yöntemi
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: be30b1ff79c2aceb97eb4ad42052da7dd162f5d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792280"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="73953-102">ICorDebugProcess6::DecodeEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73953-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="73953-103">Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarının yükünde kapsüllenmiş yönetilen hata ayıklama olaylarının kodunu çözer.</span><span class="sxs-lookup"><span data-stu-id="73953-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73953-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73953-104">Syntax</span></span>  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73953-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73953-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="73953-106">'ndaki Bir yönetilen hata ayıklama olayı hakkında bilgi içeren bir yerel özel durum ayıklama olayından bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73953-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="73953-107">'ndaki `pRecord` bayt dizisindeki öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="73953-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="73953-108">'ndaki Yönetilmeyen hata ayıklama olayının biçimini belirten [Cordebugrecordformat](cordebugrecordformat-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="73953-108">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="73953-109">'ndaki Hedef mimarisine bağlı ve hata ayıklama olayı hakkında ek bilgiler belirten bir bit alanı.</span><span class="sxs-lookup"><span data-stu-id="73953-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="73953-110">Windows sistemleri için, [Cordebugdecodeeventflagswindows](cordebugdecodeeventflagswindows-enumeration.md) sabit listesinin bir üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="73953-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="73953-111">'ndaki Özel durumun oluşturulduğu iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="73953-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="73953-112">dışı Kodu çözülmüş bir yönetilen hata ayıklama olayını temsil eden [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73953-112">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73953-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73953-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73953-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73953-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73953-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73953-115">Requirements</span></span>  
 <span data-ttu-id="73953-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73953-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73953-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73953-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73953-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="73953-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73953-119">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73953-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73953-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73953-120">See also</span></span>

- [<span data-ttu-id="73953-121">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73953-121">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="73953-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="73953-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
