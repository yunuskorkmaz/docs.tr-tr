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
ms.openlocfilehash: 99fc89d1aee6c9f0fbffc193e12ce563e820f268
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789278"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="ecd3d-102">CorDebugRecordFormat Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ecd3d-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="ecd3d-103">Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd3d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecd3d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="ecd3d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ecd3d-105">Members</span></span>  
  
|<span data-ttu-id="ecd3d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ecd3d-106">Member</span></span>|<span data-ttu-id="ecd3d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecd3d-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="ecd3d-108">Veriler 32 bitlik bir Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="ecd3d-109">Veriler 64 bitlik bir Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecd3d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecd3d-110">Remarks</span></span>  
 <span data-ttu-id="ecd3d-111">`CorDebugRecordFormat` numaralandırmasının bir üyesi, `pRecord` bağımsız değişkeninde bayt dizisinin biçimini göstermek için [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecd3d-112">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecd3d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecd3d-113">Requirements</span></span>  
 <span data-ttu-id="ecd3d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd3d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd3d-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ecd3d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecd3d-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ecd3d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecd3d-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecd3d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecd3d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecd3d-118">See also</span></span>

- [<span data-ttu-id="ecd3d-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ecd3d-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
