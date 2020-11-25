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
ms.openlocfilehash: 2cd362279f5c5ff281b9674fe3d1e293ddbab5f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707301"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="629d6-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="629d6-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>

<span data-ttu-id="629d6-103">Belirli bir belgedeki Yöntem için en küçük başlangıç satırını ve en büyük bitiş satırını alır.</span><span class="sxs-lookup"><span data-stu-id="629d6-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="629d6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="629d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="629d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="629d6-105">Parameters</span></span>  

 `document`  
 <span data-ttu-id="629d6-106">'ndaki Belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="629d6-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="629d6-107">dışı `ULONG32` Başlangıç satırını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="629d6-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="629d6-108">dışı `ULONG32` Bitiş satırını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="629d6-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="629d6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="629d6-109">Return Value</span></span>  

 <span data-ttu-id="629d6-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="629d6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="629d6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="629d6-111">Requirements</span></span>  

 <span data-ttu-id="629d6-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="629d6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="629d6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="629d6-113">See also</span></span>

- [<span data-ttu-id="629d6-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="629d6-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
