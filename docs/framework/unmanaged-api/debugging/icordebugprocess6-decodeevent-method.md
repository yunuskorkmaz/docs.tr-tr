---
title: ICorDebugProcess6::DecodeEvent Yöntemi
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: a0b77724a5a70461073d554a9794c5a904f6a363
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178575"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="63c2c-102">ICorDebugProcess6::DecodeEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63c2c-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="63c2c-103">Özel olarak hazırlanmış yerel özel durum hata ayıklama olaylarının yükünde kapsüllenmiş yönetilen hata ayıklama olaylarını çözme.</span><span class="sxs-lookup"><span data-stu-id="63c2c-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63c2c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="63c2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63c2c-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="63c2c-106">[içinde] Yönetilen hata ayıklama olayı hakkında bilgi içeren yerel bir özel durum hata ayıklama olayından bir bayt diziiçin işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63c2c-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="63c2c-107">[içinde] Bayt dizisindeki `pRecord` öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="63c2c-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="63c2c-108">[içinde] Yönetilmeyen hata ayıklama olayının biçimini belirten [bir CorDebugRecordFormat](cordebugrecordformat-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="63c2c-108">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="63c2c-109">[içinde] Hedef mimariye bağlı olan ve hata ayıklama olayı hakkında ek bilgiler belirten bir bit alanı.</span><span class="sxs-lookup"><span data-stu-id="63c2c-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="63c2c-110">Windows sistemleri için, [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) numaralandırma üyesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="63c2c-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="63c2c-111">[içinde] Özel durum atıldığı iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="63c2c-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="63c2c-112">[çıkış] Çözülmüş yönetilen hata ayıklama olayını temsil eden bir [ICorDebugDebugEvent](icordebugdebugevent-interface.md) nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63c2c-112">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63c2c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63c2c-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63c2c-114">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63c2c-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c2c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63c2c-115">Requirements</span></span>  
 <span data-ttu-id="63c2c-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c2c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c2c-117">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63c2c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63c2c-118">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63c2c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63c2c-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c2c-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c2c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63c2c-120">See also</span></span>

- [<span data-ttu-id="63c2c-121">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63c2c-121">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="63c2c-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="63c2c-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
