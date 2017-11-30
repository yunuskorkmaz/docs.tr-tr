---
title: ISymENCUnmanagedMethod::GetLineFromOffset Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f18357b3a58a5409da93d4d2491997e9ca1cc70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="497ce-102">ISymENCUnmanagedMethod::GetLineFromOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="497ce-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="497ce-103">Bir uzaklık ile ilişkili satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="497ce-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="497ce-104">Varsa uzaklık parametresi (`dwOffset`) bir dizi noktası değil Bu yöntem önceki uzaklık ile ilişkili satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="497ce-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="497ce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="497ce-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="497ce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="497ce-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="497ce-107">[in] A `ULONG32` uzaklık içerir.</span><span class="sxs-lookup"><span data-stu-id="497ce-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="497ce-108">[out] Bir işaretçi bir `ULONG32` satır alır.</span><span class="sxs-lookup"><span data-stu-id="497ce-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="497ce-109">[out] Bir işaretçi bir `ULONG32` sütunu alır.</span><span class="sxs-lookup"><span data-stu-id="497ce-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="497ce-110">[out] Bir işaretçi bir `ULONG32` satır sonu alır.</span><span class="sxs-lookup"><span data-stu-id="497ce-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="497ce-111">[out] Bir işaretçi bir `ULONG32` end sütunu alır.</span><span class="sxs-lookup"><span data-stu-id="497ce-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="497ce-112">[out] Bir işaretçi bir `ULONG32` ilişkili dizi noktası alır.</span><span class="sxs-lookup"><span data-stu-id="497ce-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="497ce-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="497ce-113">Return Value</span></span>  
 <span data-ttu-id="497ce-114">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="497ce-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="497ce-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="497ce-115">Requirements</span></span>  
 <span data-ttu-id="497ce-116">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="497ce-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497ce-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="497ce-117">See Also</span></span>  
 [<span data-ttu-id="497ce-118">Isymencunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="497ce-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
