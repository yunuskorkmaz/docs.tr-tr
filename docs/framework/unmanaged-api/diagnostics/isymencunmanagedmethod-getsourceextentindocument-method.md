---
description: 'Şu konuda daha fazla bilgi edinin: ıvmencunmanagedmethod:: GetSourceExtentInDocument yöntemi'
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 6fa9edb524a59b4420ebc737eb8d34eaf0c5c873
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737889"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="a7e38-103">ISymENCUnmanagedMethod::GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7e38-103">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>

<span data-ttu-id="a7e38-104">Belirli bir belgedeki Yöntem için en küçük başlangıç satırını ve en büyük bitiş satırını alır.</span><span class="sxs-lookup"><span data-stu-id="a7e38-104">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e38-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7e38-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7e38-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7e38-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="a7e38-107">'ndaki Belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7e38-107">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="a7e38-108">dışı `ULONG32` Başlangıç satırını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a7e38-108">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="a7e38-109">dışı `ULONG32` Bitiş satırını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a7e38-109">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7e38-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7e38-110">Return Value</span></span>  

 <span data-ttu-id="a7e38-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a7e38-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e38-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7e38-112">Requirements</span></span>  

 <span data-ttu-id="a7e38-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a7e38-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e38-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e38-114">See also</span></span>

- [<span data-ttu-id="a7e38-115">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7e38-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
