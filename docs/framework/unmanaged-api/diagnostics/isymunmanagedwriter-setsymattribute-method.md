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
ms.openlocfilehash: 8ffcc3a079e7e9a9d69622dc6666bb0e7641d4e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650784"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="22377-102">ISymUnmanagedWriter::SetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22377-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="22377-103">Adını alan özel bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22377-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="22377-104">Bu öznitelikler, sembol deposundaki özel meta veri öznitelikleri aksine tutulur.</span><span class="sxs-lookup"><span data-stu-id="22377-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22377-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22377-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22377-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22377-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="22377-107">[in] Öznitelik tanımlanmakta olan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="22377-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="22377-108">[in] Bir işaretçi bir `WCHAR` , öznitelik adı içerir.</span><span class="sxs-lookup"><span data-stu-id="22377-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="22377-109">[in] A `ULONG32` boyutunu gösteren `data` dizisi.</span><span class="sxs-lookup"><span data-stu-id="22377-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="22377-110">[in] Öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="22377-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22377-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="22377-111">Return Value</span></span>  
 <span data-ttu-id="22377-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="22377-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22377-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22377-113">Requirements</span></span>  
 <span data-ttu-id="22377-114">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="22377-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22377-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22377-115">See also</span></span>

- [<span data-ttu-id="22377-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22377-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
