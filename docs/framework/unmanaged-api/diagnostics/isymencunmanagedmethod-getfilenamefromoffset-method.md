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
ms.openlocfilehash: 857410187edf1c712865626a3327dd4c92cc211f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441935"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="7dd3a-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd3a-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="7dd3a-103">Bir uzaklığa ilişkin dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="7dd3a-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd3a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7dd3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dd3a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7dd3a-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="7dd3a-106">'ndaki `ULONG32`Bu, sapmayı içeren bir.</span><span class="sxs-lookup"><span data-stu-id="7dd3a-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7dd3a-107">'ndaki `ULONG32`Arabellek boyutunu belirten bir `szName` .</span><span class="sxs-lookup"><span data-stu-id="7dd3a-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7dd3a-108">dışı `ULONG32`Dosya adlarını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7dd3a-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="7dd3a-109">dışı Dosya adlarını içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="7dd3a-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dd3a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7dd3a-110">Return Value</span></span>  
 <span data-ttu-id="7dd3a-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7dd3a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd3a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7dd3a-112">Requirements</span></span>  
 <span data-ttu-id="7dd3a-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7dd3a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd3a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd3a-114">See also</span></span>

- [<span data-ttu-id="7dd3a-115">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7dd3a-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
