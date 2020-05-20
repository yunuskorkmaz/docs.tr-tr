---
title: ISymUnmanagedAsyncMethod Arabirimi
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: fef1af75587b889afad9cb5b93d0cd722294006b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441818"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="7dfe5-102">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7dfe5-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="7dfe5-103">Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dfe5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7dfe5-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="7dfe5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7dfe5-105">Methods</span></span>  
 <span data-ttu-id="7dfe5-106">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="7dfe5-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="7dfe5-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7dfe5-107">Method</span></span>|<span data-ttu-id="7dfe5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dfe5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7dfe5-109">GetAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dfe5-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="7dfe5-110">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="7dfe5-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="7dfe5-111">GetAsyncStepInfoCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dfe5-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="7dfe5-112">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="7dfe5-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="7dfe5-113">GetCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dfe5-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="7dfe5-114">Bkz. [Definecatch Handlerılsapmasını metodu](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="7dfe5-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="7dfe5-115">GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dfe5-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="7dfe5-116">Bkz. [DefineKickoffMethod Yöntemi](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="7dfe5-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="7dfe5-117">HasCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dfe5-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="7dfe5-118">Bkz. [Definecatch Handlerılsapmasını metodu](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="7dfe5-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="7dfe5-119">IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dfe5-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="7dfe5-120">Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="7dfe5-121">Bu yöntem döndürürse `FALSE` , bu arabirimdeki diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="7dfe5-122">Hepsi `E_UNEXPECTED` Bu durumda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7dfe5-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7dfe5-123">Requirements</span></span>  
 <span data-ttu-id="7dfe5-124">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7dfe5-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfe5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-125">See also</span></span>

- [<span data-ttu-id="7dfe5-126">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7dfe5-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
