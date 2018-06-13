---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset Metodu
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
ms.openlocfilehash: db3e9cfa73672920ff70d9128541a8f513fca00f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432662"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="9b148-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="9b148-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="9b148-103">Bir uzaklık ile ilişkili satırı dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="9b148-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b148-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b148-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b148-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b148-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="9b148-106">[in] A `ULONG32` uzaklık içerir.</span><span class="sxs-lookup"><span data-stu-id="9b148-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9b148-107">[in] A `ULONG32` boyutunu gösterir `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="9b148-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9b148-108">[out] Bir işaretçi bir `ULONG32` karakter dosya adlarını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="9b148-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="9b148-109">[out] Dosya adlarını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="9b148-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b148-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9b148-110">Return Value</span></span>  
 <span data-ttu-id="9b148-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9b148-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b148-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b148-112">Requirements</span></span>  
 <span data-ttu-id="9b148-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9b148-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b148-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b148-114">See Also</span></span>  
 [<span data-ttu-id="9b148-115">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b148-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
