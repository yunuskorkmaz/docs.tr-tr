---
title: ISymUnmanagedMethod::GetRanges Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32036058924aaf79fa7282144ced75040bc1f825
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426027"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="d4f3a-102">ISymUnmanagedMethod::GetRanges Metodu</span><span class="sxs-lookup"><span data-stu-id="d4f3a-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="d4f3a-103">Bir konumda bir belge, bu yöntem içinde konumu kapsayan Microsoft Ara dili (MSIL) aralıklarına karşılık gelir başlangıç ve bitiş uzaklığında çiftleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="d4f3a-104">Dizi dizisi ve [Başlangıç, son, Başlat, son] biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="d4f3a-105">2 ile bölünmüş dizi uzunluğu, aralığı çiftleri sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f3a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4f3a-106">Syntax</span></span>  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4f3a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4f3a-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="d4f3a-108">[in] Uzaklık istenen belge.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="d4f3a-109">[in] Aralıklarına karşılık gelen belge satırı.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="d4f3a-110">[in] Aralıklarına karşılık gelen belge sütun.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="d4f3a-111">[in] Boyutunu `ranges` dizi.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="d4f3a-112">[out] Bir işaretçi bir `ULONG32` aralıkları içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="d4f3a-113">[out] Aralıkları alır arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4f3a-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d4f3a-114">Return Value</span></span>  
 <span data-ttu-id="d4f3a-115">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f3a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4f3a-116">Requirements</span></span>  
 <span data-ttu-id="d4f3a-117">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d4f3a-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f3a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4f3a-118">See Also</span></span>  
 [<span data-ttu-id="d4f3a-119">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4f3a-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
