---
title: ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d83270d0e7f5dabff8402f5f81dae20d4457d147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604264"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="293a1-102">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="293a1-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="293a1-103">Her yöntem simge için isteğe bağlı zaman uyumsuz yöntem bilgilerini tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="293a1-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="293a1-104">Her zaman açık bir yöntemle kullanın. diğer bir deyişle, yapılan çağrılar arasında [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="293a1-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="293a1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="293a1-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="293a1-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="293a1-106">Methods</span></span>  
 <span data-ttu-id="293a1-107">Bu arabirimi aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="293a1-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="293a1-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="293a1-108">Method</span></span>|<span data-ttu-id="293a1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="293a1-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="293a1-110">DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="293a1-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="293a1-111">Zaman uyumsuz grubu tanımlamanız geçerli yöntemi işlemleri bekler.</span><span class="sxs-lookup"><span data-stu-id="293a1-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="293a1-112">Her yield uzaklığı olası yield tanımlayan bir await'ın dönüş yönergesi, eşleşir.</span><span class="sxs-lookup"><span data-stu-id="293a1-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="293a1-113">Her `breakpointMethod` / `breakpointOffset` çifti tanımlar burada zaman uyumsuz işlemi devam edecek; farklı bir yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="293a1-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="293a1-114">DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="293a1-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="293a1-115">IL uzaklığı bir zaman uyumsuz yöntem sarmalayan derleyicinin ürettiği catch işleyicisi için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="293a1-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="293a1-116">Oluşturulan yakalama IL uzaklığı, hata ayıklayıcı tarafından kullanıcı olmayan kod gibi bir kullanıcı kodu yöntemde oluşsa yakalama işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="293a1-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="293a1-117">Özellikle, yanıt olarak kullanılır bir **CatchHandlerFound** özel durum olayı.</span><span class="sxs-lookup"><span data-stu-id="293a1-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="293a1-118">DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="293a1-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="293a1-119">Zaman uyumsuz işlem başlattığı başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="293a1-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="293a1-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="293a1-120">Requirements</span></span>  
 <span data-ttu-id="293a1-121">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="293a1-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="293a1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="293a1-122">See also</span></span>
- [<span data-ttu-id="293a1-123">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="293a1-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
