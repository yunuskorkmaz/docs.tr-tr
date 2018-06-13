---
title: ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ec66e0064a8d6e8d4664dd8c727aa87621cfd8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427313"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="8167b-102">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8167b-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="8167b-103">Her yöntem simgesi için isteğe bağlı zaman uyumsuz yöntem bilgilerini tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8167b-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="8167b-104">Her zaman açık bir yöntemle kullanın; diğer bir deyişle, yapılan çağrılar arasında [OpenMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) ve [CloseMethod yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="8167b-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8167b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8167b-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="8167b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8167b-106">Methods</span></span>  
 <span data-ttu-id="8167b-107">Bu arabirim, aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8167b-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="8167b-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8167b-108">Method</span></span>|<span data-ttu-id="8167b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8167b-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8167b-110">DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8167b-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="8167b-111">Zaman uyumsuz grubu tanımlayın geçerli yöntemi işlemlerinde bekler.</span><span class="sxs-lookup"><span data-stu-id="8167b-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="8167b-112">Her verim uzaklığı potansiyel verimini tanımlayan bir bekleme 's dönüş yönerge eşleşir.</span><span class="sxs-lookup"><span data-stu-id="8167b-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="8167b-113">Her `breakpointMethod` / `breakpointOffset` çifti tanımlar burada zaman uyumsuz işlemi devam edecek; farklı bir yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="8167b-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="8167b-114">DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8167b-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="8167b-115">Zaman uyumsuz yöntem sarmalar derleyicinin ürettiği catch işleyicisi için uzaklık IL ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8167b-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="8167b-116">Oluşturulan yakalama IL uzaklığı kullanıcı olmayan kod değilmiş gibi bir kullanıcı kodu yönteminde oluşsa da catch işleme için hata ayıklayıcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8167b-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="8167b-117">Özellikle, bu yanıt olarak kullanıldığı bir **CatchHandlerFound** özel durum olayı.</span><span class="sxs-lookup"><span data-stu-id="8167b-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="8167b-118">DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8167b-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="8167b-119">Zaman uyumsuz işlemi başlatır başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8167b-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8167b-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8167b-120">Requirements</span></span>  
 <span data-ttu-id="8167b-121">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8167b-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8167b-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8167b-122">See Also</span></span>  
 [<span data-ttu-id="8167b-123">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8167b-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
