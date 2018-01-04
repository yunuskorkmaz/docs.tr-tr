---
title: "ISymUnmanagedWriter::CloseScope Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d47be1d220729ed32fcf77a77e611003085c15d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="6a9dd-102">ISymUnmanagedWriter::CloseScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a9dd-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="6a9dd-103">Geçerli sözcük kapsamı kapatır.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a9dd-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a9dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a9dd-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="6a9dd-106">[in] Sözcük kapsamda bayt son yönergenin sonunda nokta yöntemi başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a9dd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a9dd-107">Return Value</span></span>  
 <span data-ttu-id="6a9dd-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9dd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a9dd-109">Remarks</span></span>  
 <span data-ttu-id="6a9dd-110">Bir kapsam kapatıldıktan sonra daha fazla değişken içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="6a9dd-111">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) ile kullanılan donuk kapsam tanımlayıcıyı döndürür [Isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) daha sonra bir kapsamını tanımlamak için başlangıç ve bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="6a9dd-112">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve `ISymUnmanagedWriter::CloseScope` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="6a9dd-113">Kapsam tanımlayıcıları yalnızca geçerli yöntemi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9dd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a9dd-114">Requirements</span></span>  
 <span data-ttu-id="6a9dd-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a9dd-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9dd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-116">See Also</span></span>  
 [<span data-ttu-id="6a9dd-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a9dd-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
