---
title: ISymUnmanagedReader2::GetMethodsInDocument Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28b240159c36b03b2c476f56f7e6ad7b33f20649
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142356"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="abaf7-102">ISymUnmanagedReader2::GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abaf7-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="abaf7-103">Sağlanan belge içinde satır bilgileri her yöntemin alır.</span><span class="sxs-lookup"><span data-stu-id="abaf7-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abaf7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abaf7-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abaf7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abaf7-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="abaf7-106">[in] Belge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="abaf7-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="abaf7-107">[in] A `ULONG32` boyutunu gösteren `pRetVal` dizisi.</span><span class="sxs-lookup"><span data-stu-id="abaf7-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="abaf7-108">[out] Bir işaretçi bir `ULONG32` yöntemleri içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="abaf7-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="abaf7-109">[out] Yöntemleri alan arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="abaf7-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abaf7-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="abaf7-110">Return Value</span></span>  
 <span data-ttu-id="abaf7-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="abaf7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abaf7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abaf7-112">Requirements</span></span>  
 <span data-ttu-id="abaf7-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="abaf7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abaf7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abaf7-114">See also</span></span>

- [<span data-ttu-id="abaf7-115">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abaf7-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
