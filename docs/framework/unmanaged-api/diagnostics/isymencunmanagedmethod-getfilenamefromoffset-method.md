---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 494f39855132bc4a9551b78f746517862d285034
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074735"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="f924e-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f924e-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="f924e-103">Bir uzaklık ile ilişkili satırı dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="f924e-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f924e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f924e-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f924e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f924e-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="f924e-106">[in] A `ULONG32` içeren uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f924e-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f924e-107">[in] A `ULONG32` boyutunu gösteren `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="f924e-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f924e-108">[out] Bir işaretçi bir `ULONG32` karakter dosya adlarını içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="f924e-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="f924e-109">[out] Dosya adlarını içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="f924e-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f924e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f924e-110">Return Value</span></span>  
 <span data-ttu-id="f924e-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f924e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f924e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f924e-112">Requirements</span></span>  
 <span data-ttu-id="f924e-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f924e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f924e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f924e-114">See also</span></span>

- [<span data-ttu-id="f924e-115">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f924e-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
