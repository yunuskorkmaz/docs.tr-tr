---
title: ISymUnmanagedWriter::SetSymAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ee3e96a25a224fb5b025e22fa43169a64f6c0d2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501675"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="3f7b3-102">ISymUnmanagedWriter::SetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f7b3-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="3f7b3-103">Adını alan özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="3f7b3-104">Bu öznitelikler, sembol deposundaki özel meta veri öznitelikleri aksine tutulur.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7b3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f7b3-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f7b3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f7b3-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="3f7b3-107">[in] Öznitelik tanımlanmakta olan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="3f7b3-108">[in] Bir işaretçi bir `WCHAR` , öznitelik adı içerir.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="3f7b3-109">[in] A `ULONG32` boyutunu gösteren `data` dizisi.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="3f7b3-110">[in] Öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f7b3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3f7b3-111">Return Value</span></span>  
 <span data-ttu-id="3f7b3-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f7b3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f7b3-113">Requirements</span></span>  
 <span data-ttu-id="3f7b3-114">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3f7b3-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7b3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-115">See also</span></span>
- [<span data-ttu-id="3f7b3-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f7b3-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
