---
title: ISymUnmanagedMethod::GetRanges Yöntemi
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
ms.openlocfilehash: 94ca1db2bf85f42117f686a8cb483907003927c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205855"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="b4c3c-102">ISymUnmanagedMethod::GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4c3c-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="b4c3c-103">Belgede bir konuma konumu bu yöntem içinde kapsayan Microsoft Ara dilini (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş uzaklığında Çiftler dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="b4c3c-104">Dizi tamsayı dizisi ve [Başlangıç, bitiş, başlangıç, bitiş] biçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="b4c3c-105">2 tarafından ayrılmış dizi uzunluğu aralığın çiftleri sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c3c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4c3c-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b4c3c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4c3c-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="b4c3c-108">[in] Uzaklık istendiği belge.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="b4c3c-109">[in] Aralıkları için karşılık gelen belge satır.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="b4c3c-110">[in] Aralıkları için karşılık gelen belge sütun.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="b4c3c-111">[in] Boyutu `ranges` dizisi.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="b4c3c-112">[out] Bir işaretçi bir `ULONG32` içeriyor aralıkları için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="b4c3c-113">[out] Aralık alan arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4c3c-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b4c3c-114">Return Value</span></span>  
 <span data-ttu-id="b4c3c-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4c3c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4c3c-116">Requirements</span></span>  
 <span data-ttu-id="b4c3c-117">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b4c3c-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c3c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4c3c-118">See also</span></span>

- [<span data-ttu-id="b4c3c-119">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4c3c-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
