---
description: 'Şu konuda daha fazla bilgi edinin: ıvmencunmanagedmethod:: Getfilenamefromscope yöntemi'
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
ms.openlocfilehash: 1322e55f115958a2f4b2634dfa25eff127167d54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738006"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="3b0ac-103">ISymENCUnmanagedMethod::GetFileNameFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b0ac-103">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>

<span data-ttu-id="3b0ac-104">Bir uzaklığa ilişkin dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="3b0ac-104">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b0ac-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b0ac-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b0ac-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b0ac-106">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="3b0ac-107">'ndaki `ULONG32` Bu, sapmayı içeren bir.</span><span class="sxs-lookup"><span data-stu-id="3b0ac-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3b0ac-108">'ndaki `ULONG32` Arabellek boyutunu belirten bir `szName` .</span><span class="sxs-lookup"><span data-stu-id="3b0ac-108">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3b0ac-109">dışı `ULONG32` Dosya adlarını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3b0ac-109">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="3b0ac-110">dışı Dosya adlarını içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="3b0ac-110">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b0ac-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3b0ac-111">Return Value</span></span>  

 <span data-ttu-id="3b0ac-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3b0ac-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b0ac-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b0ac-113">Requirements</span></span>  

 <span data-ttu-id="3b0ac-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3b0ac-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0ac-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b0ac-115">See also</span></span>

- [<span data-ttu-id="3b0ac-116">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b0ac-116">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
