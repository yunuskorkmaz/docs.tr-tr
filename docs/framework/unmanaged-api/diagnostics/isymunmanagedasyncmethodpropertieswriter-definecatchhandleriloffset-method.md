---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 923c85a9dff11753a338fcfd3673d3590fca607a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196755"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="4d1f5-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d1f5-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="4d1f5-103">IL uzaklığı bir zaman uyumsuz yöntem sarmalayan derleyicinin ürettiği catch işleyicisi için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="4d1f5-104">Oluşturulan yakalama IL uzaklığı, hata ayıklayıcı tarafından bir kullanıcı kodu yöntemi ortaya çıkabilecek olsa bile, kullanıcı olmayan kod gibi yakalama işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="4d1f5-105">Özellikle, yanıt olarak kullanılır bir **CatchHandlerFound** özel durum olayı.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1f5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d1f5-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d1f5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d1f5-107">Parameters</span></span>  
  
|<span data-ttu-id="4d1f5-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="4d1f5-108">Parameter</span></span>|<span data-ttu-id="4d1f5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d1f5-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="4d1f5-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d1f5-110">Return Value</span></span>  
 <span data-ttu-id="4d1f5-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d1f5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d1f5-112">Requirements</span></span>  
 <span data-ttu-id="4d1f5-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d1f5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1f5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d1f5-114">See also</span></span>

- [<span data-ttu-id="4d1f5-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d1f5-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
