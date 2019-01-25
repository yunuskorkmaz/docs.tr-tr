---
title: ISymUnmanagedAsyncMethod Arabirimi
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd7b351de8e82f9fdbe623505f86b54f6eba68d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694873"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="66752-102">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66752-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="66752-103">Bu bir arabirimdir okuma tamamlayan [Isymunmanagedasyncmethodpropertieswriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="66752-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66752-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66752-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="66752-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="66752-105">Methods</span></span>  
 <span data-ttu-id="66752-106">Bu arabirimi aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66752-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="66752-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="66752-107">Method</span></span>|<span data-ttu-id="66752-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66752-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66752-109">GetAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66752-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="66752-110">Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="66752-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="66752-111">GetAsyncStepInfoCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66752-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="66752-112">Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="66752-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="66752-113">GetCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66752-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="66752-114">Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="66752-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="66752-115">GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66752-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="66752-116">Bkz: [DefineKickoffMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="66752-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="66752-117">HasCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66752-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="66752-118">Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="66752-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="66752-119">IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66752-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="66752-120">Yöntemi zaman uyumsuz bilgi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="66752-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="66752-121">Bu yöntem döndürürse `FALSE` sonra bu arabirimde diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="66752-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="66752-122">Tüm dönüş göründükleri `E_UNEXPECTED` bu durumda.</span><span class="sxs-lookup"><span data-stu-id="66752-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66752-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66752-123">Requirements</span></span>  
 <span data-ttu-id="66752-124">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66752-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66752-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66752-125">See also</span></span>
- [<span data-ttu-id="66752-126">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="66752-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
