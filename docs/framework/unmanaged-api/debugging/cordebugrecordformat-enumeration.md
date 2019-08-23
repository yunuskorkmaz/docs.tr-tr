---
title: CorDebugRecordFormat Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6ed7d25593f9dd5d5d01f8c06024dcf8acfcfea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916483"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="febdd-102">CorDebugRecordFormat Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="febdd-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="febdd-103">Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="febdd-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="febdd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="febdd-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="febdd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="febdd-105">Members</span></span>  
  
|<span data-ttu-id="febdd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="febdd-106">Member</span></span>|<span data-ttu-id="febdd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="febdd-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="febdd-108">Veriler 32 bitlik bir Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="febdd-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="febdd-109">Veriler 64 bitlik bir Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="febdd-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="febdd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="febdd-110">Remarks</span></span>  
 <span data-ttu-id="febdd-111">Bir `CorDebugRecordFormat` numaralandırma üyesi, `pRecord` bağımsız değişkeninde bayt dizisinin biçimini göstermek için [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="febdd-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="febdd-112">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="febdd-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="febdd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="febdd-113">Requirements</span></span>  
 <span data-ttu-id="febdd-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="febdd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="febdd-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="febdd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="febdd-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="febdd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="febdd-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="febdd-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="febdd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="febdd-118">See also</span></span>

- [<span data-ttu-id="febdd-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="febdd-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
