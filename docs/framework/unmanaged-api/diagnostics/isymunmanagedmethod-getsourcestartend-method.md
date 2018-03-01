---
title: ISymUnmanagedMethod::GetSourceStartEnd Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2bdc044d4560b616bd6eeb8d642567add1f659f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="6ebfb-102">ISymUnmanagedMethod::GetSourceStartEnd Metodu</span><span class="sxs-lookup"><span data-stu-id="6ebfb-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="6ebfb-103">Bu yöntem kaynak için başlangıç ve bitiş belge konumlarına alır.</span><span class="sxs-lookup"><span data-stu-id="6ebfb-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="6ebfb-104">İlk dizi konum başlangıç ve bitiş ikinci dizi konumdur.</span><span class="sxs-lookup"><span data-stu-id="6ebfb-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ebfb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ebfb-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ebfb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ebfb-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="6ebfb-107">[in] Başlangıç ve bitiş kaynak belgeleri.</span><span class="sxs-lookup"><span data-stu-id="6ebfb-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="6ebfb-108">[in] Başlangıç ve ilgili satırları bitiş belgeleri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="6ebfb-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="6ebfb-109">[in] Başlangıç ve ilgili sütunları bitiş belgeleri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="6ebfb-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6ebfb-110">[out] `true` konumları, tanımlanmış Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="6ebfb-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ebfb-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6ebfb-111">Return Value</span></span>  
 <span data-ttu-id="6ebfb-112">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6ebfb-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ebfb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ebfb-113">Requirements</span></span>  
 <span data-ttu-id="6ebfb-114">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ebfb-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebfb-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ebfb-115">See Also</span></span>  
 [<span data-ttu-id="6ebfb-116">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ebfb-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
