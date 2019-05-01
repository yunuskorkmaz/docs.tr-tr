---
title: ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3106c6680750826306cffb31e599ee2260bf4ad7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940302"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="4320c-102">ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4320c-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="4320c-103">Bir uzaklık ile ilişkili satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="4320c-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="4320c-104">Varsa uzaklık parametresi (`dwOffset`) bir dizi noktası değil. Bu yöntem, önceki uzaklığı ile ilişkili satır bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="4320c-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4320c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4320c-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4320c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4320c-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="4320c-107">[in] A `ULONG32` içeren uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="4320c-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="4320c-108">[out] Bir işaretçi bir `ULONG32` , satır alır.</span><span class="sxs-lookup"><span data-stu-id="4320c-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="4320c-109">[out] Bir işaretçi bir `ULONG32` , sütunu alır.</span><span class="sxs-lookup"><span data-stu-id="4320c-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="4320c-110">[out] Bir işaretçi bir `ULONG32` , satır sonunu alır.</span><span class="sxs-lookup"><span data-stu-id="4320c-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="4320c-111">[out] Bir işaretçi bir `ULONG32` , end sütunu alır.</span><span class="sxs-lookup"><span data-stu-id="4320c-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="4320c-112">[out] Bir işaretçi bir `ULONG32` , ilişkili dizi noktası alır.</span><span class="sxs-lookup"><span data-stu-id="4320c-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4320c-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4320c-113">Return Value</span></span>  
 <span data-ttu-id="4320c-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4320c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4320c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4320c-115">Requirements</span></span>  
 <span data-ttu-id="4320c-116">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4320c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4320c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4320c-117">See also</span></span>

- [<span data-ttu-id="4320c-118">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4320c-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
