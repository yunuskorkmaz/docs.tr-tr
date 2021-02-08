---
description: 'Daha fazla bilgi edinin: CorDebugRecordFormat numaralandırması'
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
ms.openlocfilehash: 856522497a8f858abdb39ac232fb3034d4d91dfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801572"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="76a8a-103">CorDebugRecordFormat Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="76a8a-103">CorDebugRecordFormat Enumeration</span></span>

<span data-ttu-id="76a8a-104">Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="76a8a-104">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a8a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="76a8a-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="76a8a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="76a8a-106">Members</span></span>  
  
|<span data-ttu-id="76a8a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="76a8a-107">Member</span></span>|<span data-ttu-id="76a8a-108">Description</span><span class="sxs-lookup"><span data-stu-id="76a8a-108">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="76a8a-109">Veriler 32 bitlik bir Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="76a8a-109">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="76a8a-110">Veriler 64 bitlik bir Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="76a8a-110">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76a8a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76a8a-111">Remarks</span></span>  

 <span data-ttu-id="76a8a-112">Bir numaralandırma üyesi, `CorDebugRecordFormat` bağımsız değişkeninde bayt dizisinin biçimini göstermek Için [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemine geçirilir `pRecord` .</span><span class="sxs-lookup"><span data-stu-id="76a8a-112">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76a8a-113">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="76a8a-113">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76a8a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76a8a-114">Requirements</span></span>  

 <span data-ttu-id="76a8a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76a8a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76a8a-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76a8a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76a8a-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="76a8a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76a8a-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76a8a-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a8a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76a8a-119">See also</span></span>

- [<span data-ttu-id="76a8a-120">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="76a8a-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
