---
title: ISymUnmanagedReader2::GetMethodsInDocument Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetMethodsInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 15053aeb3febd533a6977ef446fc1aa3bd8a92b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="284fa-102">ISymUnmanagedReader2::GetMethodsInDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="284fa-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="284fa-103">Sağlanan belgede satırı bilgileri içeren her yöntem alır.</span><span class="sxs-lookup"><span data-stu-id="284fa-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="284fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="284fa-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="284fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="284fa-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="284fa-106">[in] Belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="284fa-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="284fa-107">[in] A `ULONG32` boyutunu gösterir `pRetVal` dizi.</span><span class="sxs-lookup"><span data-stu-id="284fa-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="284fa-108">[out] Bir işaretçi bir `ULONG32` yöntemleri içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="284fa-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="284fa-109">[out] Yöntemleri alır arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="284fa-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="284fa-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="284fa-110">Return Value</span></span>  
 <span data-ttu-id="284fa-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="284fa-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="284fa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="284fa-112">Requirements</span></span>  
 <span data-ttu-id="284fa-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="284fa-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="284fa-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="284fa-114">See Also</span></span>  
 [<span data-ttu-id="284fa-115">Isymunmanagedreader2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="284fa-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
