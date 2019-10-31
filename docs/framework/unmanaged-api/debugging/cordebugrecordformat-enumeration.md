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
ms.openlocfilehash: 239b1a9f258f435e6dcca6e00cc20df5b5c01188
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097449"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="238ff-102">CorDebugRecordFormat Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="238ff-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="238ff-103">Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="238ff-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="238ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="238ff-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="238ff-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="238ff-105">Members</span></span>  
  
|<span data-ttu-id="238ff-106">Üye</span><span class="sxs-lookup"><span data-stu-id="238ff-106">Member</span></span>|<span data-ttu-id="238ff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="238ff-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="238ff-108">Veriler 32 bitlik bir Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="238ff-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="238ff-109">Veriler 64 bitlik bir Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="238ff-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="238ff-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="238ff-110">Remarks</span></span>  
 <span data-ttu-id="238ff-111">`CorDebugRecordFormat` numaralandırmasının bir üyesi, `pRecord` bağımsız değişkeninde bayt dizisinin biçimini göstermek için [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="238ff-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="238ff-112">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="238ff-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="238ff-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="238ff-113">Requirements</span></span>  
 <span data-ttu-id="238ff-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="238ff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="238ff-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="238ff-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="238ff-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="238ff-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="238ff-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="238ff-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238ff-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="238ff-118">See also</span></span>

- [<span data-ttu-id="238ff-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="238ff-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
