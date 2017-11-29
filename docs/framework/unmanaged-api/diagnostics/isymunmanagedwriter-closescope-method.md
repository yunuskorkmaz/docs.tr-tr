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
ms.openlocfilehash: a8df22e5f9ea2ca294f502fcebf4b2ed5cd7900d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="090c6-102">ISymUnmanagedWriter::CloseScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="090c6-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="090c6-103">Geçerli sözcük kapsamı kapatır.</span><span class="sxs-lookup"><span data-stu-id="090c6-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="090c6-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="090c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="090c6-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="090c6-106">[in] Sözcük kapsamda bayt son yönergenin sonunda nokta yöntemi başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="090c6-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="090c6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="090c6-107">Return Value</span></span>  
 <span data-ttu-id="090c6-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="090c6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="090c6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="090c6-109">Remarks</span></span>  
 <span data-ttu-id="090c6-110">Bir kapsam kapatıldıktan sonra daha fazla değişken içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="090c6-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="090c6-111">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) ile kullanılan donuk kapsam tanımlayıcıyı döndürür [Isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) daha sonra bir kapsamını tanımlamak için başlangıç ve bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="090c6-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="090c6-112">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve `ISymUnmanagedWriter::CloseScope` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="090c6-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="090c6-113">Kapsam tanımlayıcıları yalnızca geçerli yöntemi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="090c6-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="090c6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="090c6-114">Requirements</span></span>  
 <span data-ttu-id="090c6-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="090c6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="090c6-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="090c6-116">See Also</span></span>  
 [<span data-ttu-id="090c6-117">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
