---
title: ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 04876483fd42e3f6e55222416fd0747891734a52
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501865"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="1b8bd-102">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b8bd-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="1b8bd-103">Her yöntem sembolü için isteğe bağlı zaman uyumsuz yöntem bilgilerini tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="1b8bd-104">Her zaman açık bir yöntemle kullanın; diğer bir deyişle, [OpenMethod yöntemi](isymunmanagedwriter-openmethod-method.md) ve [CloseMethod yöntemi](isymunmanagedwriter-closemethod-method.md)çağrıları arasında.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b8bd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b8bd-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="1b8bd-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1b8bd-106">Methods</span></span>  
 <span data-ttu-id="1b8bd-107">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="1b8bd-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="1b8bd-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1b8bd-108">Method</span></span>|<span data-ttu-id="1b8bd-109">Description</span><span class="sxs-lookup"><span data-stu-id="1b8bd-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b8bd-110">DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b8bd-110">DefineAsyncStepInfo Method</span></span>](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="1b8bd-111">Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="1b8bd-112">Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="1b8bd-113">Her bir `breakpointMethod` / `breakpointOffset` çift zaman uyumsuz işlemin hangi noktada sürdürüleceği tanımlar; farklı bir yöntemde olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="1b8bd-114">DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b8bd-114">DefineCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="1b8bd-115">Bir zaman uyumsuz yöntemi sarmalayan derleyicinin ürettiği catch işleyicisinin Il sapmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="1b8bd-116">Oluşturulan catch 'in Il kayması, hata ayıklayıcı tarafından, Kullanıcı kodu yönteminde meydana gelse bile, Kullanıcı olmayan kod gibi catch 'i işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="1b8bd-117">Özellikle, bir **catch Handlerfound** özel durum olayına yanıt olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="1b8bd-118">DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b8bd-118">DefineKickoffMethod Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="1b8bd-119">Zaman uyumsuz işlemi başlatan başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b8bd-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b8bd-120">Requirements</span></span>  
 <span data-ttu-id="1b8bd-121">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1b8bd-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b8bd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b8bd-122">See also</span></span>

- [<span data-ttu-id="1b8bd-123">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b8bd-123">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
