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
ms.openlocfilehash: c2f8397382dde061078a0d96114420f1c5f48669
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="69dbf-102">CorDebugRecordFormat Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="69dbf-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="69dbf-103">Yerel özel durum hata ayıklama olay hakkında bilgi içeren bir bayt dizisi verilerin biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="69dbf-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69dbf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69dbf-104">Syntax</span></span>  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="69dbf-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="69dbf-105">Members</span></span>  
  
|<span data-ttu-id="69dbf-106">Üye</span><span class="sxs-lookup"><span data-stu-id="69dbf-106">Member</span></span>|<span data-ttu-id="69dbf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69dbf-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="69dbf-108">Verileri bir 32 bit Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="69dbf-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="69dbf-109">Verileri bir 64-bit Windows özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="69dbf-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69dbf-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69dbf-110">Remarks</span></span>  
 <span data-ttu-id="69dbf-111">Üye `CorDebugRecordFormat` numaralandırma iletilir [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) bayt dizisi biçimini belirtmek için yöntemi kendi `pRecord` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="69dbf-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69dbf-112">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="69dbf-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69dbf-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69dbf-113">Requirements</span></span>  
 <span data-ttu-id="69dbf-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69dbf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69dbf-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69dbf-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69dbf-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69dbf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69dbf-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69dbf-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69dbf-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69dbf-118">See Also</span></span>  
 [<span data-ttu-id="69dbf-119">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="69dbf-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
