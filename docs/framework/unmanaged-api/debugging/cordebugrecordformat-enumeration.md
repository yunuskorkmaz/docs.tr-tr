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
ms.openlocfilehash: add1458bb3a50a5e5433e8cc7baaf47d750c927d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083679"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="e3348-102">CorDebugRecordFormat Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e3348-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="e3348-103">Yerel özel durum hata ayıklama olayla ilgili bilgileri içeren bir bayt dizisi verilerinin biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3348-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3348-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3348-104">Syntax</span></span>  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="e3348-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e3348-105">Members</span></span>  
  
|<span data-ttu-id="e3348-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e3348-106">Member</span></span>|<span data-ttu-id="e3348-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3348-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="e3348-108">Verileri bir 32 bit Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="e3348-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="e3348-109">Verileri bir 64 bit Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="e3348-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3348-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3348-110">Remarks</span></span>  
 <span data-ttu-id="e3348-111">Üye `CorDebugRecordFormat` numaralandırma geçirilen [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) bayt dizisindeki biçimini belirtmek için yöntemi kendi `pRecord` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="e3348-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3348-112">Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e3348-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3348-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3348-113">Requirements</span></span>  
 <span data-ttu-id="e3348-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3348-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3348-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3348-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3348-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3348-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3348-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3348-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3348-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3348-118">See also</span></span>

- [<span data-ttu-id="e3348-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e3348-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
