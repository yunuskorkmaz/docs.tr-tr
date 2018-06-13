---
title: ISymUnmanagedWriter::CloseScope Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a11f689f1fa93e1122ffcc78187c4287db7ea534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427030"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="ba7b7-102">ISymUnmanagedWriter::CloseScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba7b7-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="ba7b7-103">Geçerli sözcük kapsamı kapatır.</span><span class="sxs-lookup"><span data-stu-id="ba7b7-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba7b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba7b7-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba7b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba7b7-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="ba7b7-106">[in] Sözcük kapsamda bayt son yönergenin sonunda nokta yöntemi başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="ba7b7-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba7b7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba7b7-107">Return Value</span></span>  
 <span data-ttu-id="ba7b7-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ba7b7-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba7b7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba7b7-109">Remarks</span></span>  
 <span data-ttu-id="ba7b7-110">Bir kapsam kapatıldıktan sonra daha fazla değişken içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ba7b7-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="ba7b7-111">[Isymunmanagedwriter::openscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) ile kullanılan donuk kapsam tanımlayıcıyı döndürür [Isymunmanagedwriter::setscoperange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) daha sonra bir kapsamını tanımlamak için başlangıç ve bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="ba7b7-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="ba7b7-112">Uzaklık bu durumda, geçirilen `ISymUnmanagedWriter::OpenScope` ve `ISymUnmanagedWriter::CloseScope` göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="ba7b7-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="ba7b7-113">Kapsam tanımlayıcıları yalnızca geçerli yöntemi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="ba7b7-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba7b7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba7b7-114">Requirements</span></span>  
 <span data-ttu-id="ba7b7-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ba7b7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba7b7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba7b7-116">See Also</span></span>  
 [<span data-ttu-id="ba7b7-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba7b7-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
