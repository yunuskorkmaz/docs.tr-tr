---
title: ISymUnmanagedReader2::GetMethodsInDocument Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 762649e260817c43291de416d2f1a92a8f03afb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427375"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="1a31b-102">ISymUnmanagedReader2::GetMethodsInDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="1a31b-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="1a31b-103">Sağlanan belgede satırı bilgileri içeren her yöntem alır.</span><span class="sxs-lookup"><span data-stu-id="1a31b-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a31b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a31b-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a31b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a31b-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="1a31b-106">[in] Belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a31b-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="1a31b-107">[in] A `ULONG32` boyutunu gösterir `pRetVal` dizi.</span><span class="sxs-lookup"><span data-stu-id="1a31b-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="1a31b-108">[out] Bir işaretçi bir `ULONG32` yöntemleri içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="1a31b-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1a31b-109">[out] Yöntemleri alır arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a31b-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a31b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a31b-110">Return Value</span></span>  
 <span data-ttu-id="1a31b-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1a31b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a31b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a31b-112">Requirements</span></span>  
 <span data-ttu-id="1a31b-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1a31b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a31b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a31b-114">See Also</span></span>  
 [<span data-ttu-id="1a31b-115">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a31b-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
