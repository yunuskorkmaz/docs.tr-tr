---
title: "CorDebugRecordFormat Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugRecordFormat
api_location: mscordbi.dll
api_type: COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaf962250d97f031eaa60b7cc0b15622897aad3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="56b08-102">CorDebugRecordFormat Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="56b08-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="56b08-103">Yerel özel durum hata ayıklama olay hakkında bilgi içeren bir bayt dizisi verilerin biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="56b08-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56b08-104">Syntax</span></span>  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="56b08-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="56b08-105">Members</span></span>  
  
|<span data-ttu-id="56b08-106">Üye</span><span class="sxs-lookup"><span data-stu-id="56b08-106">Member</span></span>|<span data-ttu-id="56b08-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56b08-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="56b08-108">Verileri bir 32 bit Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="56b08-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="56b08-109">Verileri bir 64-bit Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="56b08-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56b08-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56b08-110">Remarks</span></span>  
 <span data-ttu-id="56b08-111">Üye `CorDebugRecordFormat` numaralandırma iletilir [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) bayt dizisi biçimini belirtmek için yöntemi kendi `pRecord` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="56b08-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56b08-112">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="56b08-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56b08-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56b08-113">Requirements</span></span>  
 <span data-ttu-id="56b08-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56b08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56b08-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56b08-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56b08-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56b08-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56b08-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56b08-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b08-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56b08-118">See Also</span></span>  
 [<span data-ttu-id="56b08-119">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="56b08-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
