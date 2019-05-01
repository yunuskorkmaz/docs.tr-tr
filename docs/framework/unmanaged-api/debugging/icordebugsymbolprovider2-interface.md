---
title: ICorDebugSymbolProvider2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b787302902779695c48df6e02e2ee00b28f44cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994116"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="27033-102">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27033-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="27033-103">Mantıksal olarak genişletir [Icordebugsymbolprovider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) ek hata ayıklama bilgilerini almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="27033-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27033-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="27033-104">Methods</span></span>  
  
|<span data-ttu-id="27033-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="27033-105">Method</span></span>|<span data-ttu-id="27033-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27033-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27033-107">GetFrameProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27033-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="27033-108">Bir yöntemi ve üst çerçevenin bir kod göreli sanal adres verilen göreli sanal adres başlangıç yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="27033-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="27033-109">GetGenericDictionaryInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27033-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="27033-110">Genel bir sözlük harita alır.</span><span class="sxs-lookup"><span data-stu-id="27033-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27033-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27033-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27033-112">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="27033-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="27033-113">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="27033-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27033-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27033-114">Requirements</span></span>  
 <span data-ttu-id="27033-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27033-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27033-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27033-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27033-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27033-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27033-118">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27033-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27033-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27033-119">See also</span></span>

- [<span data-ttu-id="27033-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27033-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="27033-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="27033-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="27033-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="27033-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
