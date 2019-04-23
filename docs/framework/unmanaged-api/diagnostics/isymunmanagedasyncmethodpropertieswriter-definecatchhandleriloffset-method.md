---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 923c85a9dff11753a338fcfd3673d3590fca607a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196755"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="6733c-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6733c-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="6733c-103">IL uzaklığı bir zaman uyumsuz yöntem sarmalayan derleyicinin ürettiği catch işleyicisi için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6733c-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="6733c-104">Oluşturulan yakalama IL uzaklığı, hata ayıklayıcı tarafından bir kullanıcı kodu yöntemi ortaya çıkabilecek olsa bile, kullanıcı olmayan kod gibi yakalama işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6733c-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="6733c-105">Özellikle, yanıt olarak kullanılır bir **CatchHandlerFound** özel durum olayı.</span><span class="sxs-lookup"><span data-stu-id="6733c-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6733c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6733c-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6733c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6733c-107">Parameters</span></span>  
  
|<span data-ttu-id="6733c-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="6733c-108">Parameter</span></span>|<span data-ttu-id="6733c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6733c-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="6733c-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6733c-110">Return Value</span></span>  
 <span data-ttu-id="6733c-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="6733c-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6733c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6733c-112">Requirements</span></span>  
 <span data-ttu-id="6733c-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6733c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6733c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6733c-114">See also</span></span>

- [<span data-ttu-id="6733c-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6733c-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
