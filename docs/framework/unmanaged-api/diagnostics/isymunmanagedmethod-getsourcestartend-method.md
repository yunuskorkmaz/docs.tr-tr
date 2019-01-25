---
title: ISymUnmanagedMethod::GetSourceStartEnd Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ecb726f275a694fded2c486448a60b28fadb168
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561874"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="aeacb-102">ISymUnmanagedMethod::GetSourceStartEnd Metodu</span><span class="sxs-lookup"><span data-stu-id="aeacb-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="aeacb-103">Bu yöntemin kaynağı için başlangıç ve bitiş belge konumları alır.</span><span class="sxs-lookup"><span data-stu-id="aeacb-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="aeacb-104">İlk dizi konumunda başlangıç ve bitiş ikinci dizi konumdur.</span><span class="sxs-lookup"><span data-stu-id="aeacb-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeacb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aeacb-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aeacb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aeacb-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="aeacb-107">[in] Başlangıç ve bitiş kaynak belge.</span><span class="sxs-lookup"><span data-stu-id="aeacb-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="aeacb-108">[in] Başlangıç ve ilgili satırları bitiş belgeleri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="aeacb-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="aeacb-109">[in] Başlangıç ve ilgili sütunları bitiş belgeleri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="aeacb-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="aeacb-110">[out] `true` konumları, tanımlanan; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="aeacb-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aeacb-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aeacb-111">Return Value</span></span>  
 <span data-ttu-id="aeacb-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="aeacb-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeacb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aeacb-113">Requirements</span></span>  
 <span data-ttu-id="aeacb-114">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aeacb-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeacb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeacb-115">See also</span></span>
- [<span data-ttu-id="aeacb-116">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aeacb-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
