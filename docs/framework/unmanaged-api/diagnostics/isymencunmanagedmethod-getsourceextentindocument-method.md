---
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
ms.openlocfilehash: b8e72745eff09c6707afe5a5f20a1ddf38b239ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448618"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="afa1d-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afa1d-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="afa1d-103">Belirli bir belgedeki Yöntem için en küçük başlangıç satırını ve en büyük bitiş satırını alır.</span><span class="sxs-lookup"><span data-stu-id="afa1d-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa1d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afa1d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afa1d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afa1d-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="afa1d-106">'ndaki Belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="afa1d-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="afa1d-107">dışı Başlangıç satırını alan `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="afa1d-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="afa1d-108">dışı Bitiş satırını alan `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="afa1d-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afa1d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="afa1d-109">Return Value</span></span>  
 <span data-ttu-id="afa1d-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="afa1d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afa1d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afa1d-111">Requirements</span></span>  
 <span data-ttu-id="afa1d-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="afa1d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa1d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afa1d-113">See also</span></span>

- [<span data-ttu-id="afa1d-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afa1d-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
