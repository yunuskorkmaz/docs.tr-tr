---
description: 'Daha fazla bilgi edinin: ICorDebugSymbolProvider2 Interface'
title: ICorDebugSymbolProvider2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: b4eaeb29c15da979a522fb20e33a56030889d0c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659523"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="e3020-103">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3020-103">ICorDebugSymbolProvider2 Interface</span></span>

<span data-ttu-id="e3020-104">Ek hata ayıklama sembol bilgilerini almak için [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="e3020-104">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3020-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e3020-105">Methods</span></span>  
  
|<span data-ttu-id="e3020-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e3020-106">Method</span></span>|<span data-ttu-id="e3020-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3020-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3020-108">GetFrameProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3020-108">GetFrameProps Method</span></span>](icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="e3020-109">Bir yöntemin göreli sanal adresini Başlatan yöntemi ve ana çerçeveye kod göreli sanal adres verildiğinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3020-109">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="e3020-110">GetGenericDictionaryInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3020-110">GetGenericDictionaryInfo Method</span></span>](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="e3020-111">Genel sözlük eşlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="e3020-111">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3020-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3020-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3020-113">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3020-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e3020-114">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e3020-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3020-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3020-115">Requirements</span></span>  

 <span data-ttu-id="e3020-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3020-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3020-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e3020-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3020-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e3020-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3020-119">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3020-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3020-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3020-120">See also</span></span>

- [<span data-ttu-id="e3020-121">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3020-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e3020-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e3020-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e3020-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e3020-123">Debugging</span></span>](index.md)
