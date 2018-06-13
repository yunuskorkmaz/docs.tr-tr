---
title: ISymUnmanagedAsyncMethod Arabirimi
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cefad27d8b9314b45dec6100e35a54990fb591c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428005"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="4a7cb-102">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a7cb-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="4a7cb-103">Bu bir arabirimdir okuma tamamlayan [Isymunmanagedasyncmethodpropertieswriter arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4a7cb-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a7cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a7cb-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="4a7cb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4a7cb-105">Methods</span></span>  
 <span data-ttu-id="4a7cb-106">Bu arabirim, aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4a7cb-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="4a7cb-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4a7cb-107">Method</span></span>|<span data-ttu-id="4a7cb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a7cb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a7cb-109">GetAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a7cb-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="4a7cb-110">Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="4a7cb-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="4a7cb-111">GetAsyncStepInfoCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a7cb-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="4a7cb-112">Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="4a7cb-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="4a7cb-113">GetCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a7cb-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="4a7cb-114">Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="4a7cb-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="4a7cb-115">GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a7cb-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="4a7cb-116">Bkz: [DefineKickoffMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="4a7cb-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="4a7cb-117">HasCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a7cb-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="4a7cb-118">Bkz: [Definecatchhandlerıloffset yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="4a7cb-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="4a7cb-119">IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a7cb-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="4a7cb-120">Metodu zaman uyumsuz bilgi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="4a7cb-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="4a7cb-121">Bu yöntem döndürürse `FALSE` sonra da bu arabirimi diğer yöntemleri çağırmak için geçersiz.</span><span class="sxs-lookup"><span data-stu-id="4a7cb-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="4a7cb-122">Tüm iade edecek `E_UNEXPECTED` bu durumda.</span><span class="sxs-lookup"><span data-stu-id="4a7cb-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a7cb-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a7cb-123">Requirements</span></span>  
 <span data-ttu-id="4a7cb-124">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4a7cb-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7cb-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a7cb-125">See Also</span></span>  
 [<span data-ttu-id="4a7cb-126">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a7cb-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
