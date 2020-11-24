---
title: ICorDebugSymbolProvider2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: 3bef03e9e85224058bc17e1f0ce8746e98aa30f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688347"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="95ce1-102">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95ce1-102">ICorDebugSymbolProvider2 Interface</span></span>

<span data-ttu-id="95ce1-103">Ek hata ayıklama sembol bilgilerini almak için [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="95ce1-103">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95ce1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="95ce1-104">Methods</span></span>  
  
|<span data-ttu-id="95ce1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="95ce1-105">Method</span></span>|<span data-ttu-id="95ce1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95ce1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95ce1-107">GetFrameProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95ce1-107">GetFrameProps Method</span></span>](icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="95ce1-108">Bir yöntemin göreli sanal adresini Başlatan yöntemi ve ana çerçeveye kod göreli sanal adres verildiğinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="95ce1-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="95ce1-109">GetGenericDictionaryInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95ce1-109">GetGenericDictionaryInfo Method</span></span>](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="95ce1-110">Genel sözlük eşlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="95ce1-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95ce1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95ce1-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95ce1-112">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95ce1-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="95ce1-113">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="95ce1-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95ce1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95ce1-114">Requirements</span></span>  

 <span data-ttu-id="95ce1-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95ce1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95ce1-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95ce1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95ce1-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="95ce1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95ce1-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95ce1-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ce1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95ce1-119">See also</span></span>

- [<span data-ttu-id="95ce1-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95ce1-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="95ce1-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="95ce1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="95ce1-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="95ce1-122">Debugging</span></span>](index.md)
