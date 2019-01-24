---
title: ISymUnmanagedMethod::GetSequencePoints Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf6528e8fe6a979db26ae44819bf34a36592ed6b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623631"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="ab51b-102">ISymUnmanagedMethod::GetSequencePoints Metodu</span><span class="sxs-lookup"><span data-stu-id="ab51b-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="ab51b-103">Bu yöntem içinde tüm dizi noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="ab51b-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab51b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab51b-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab51b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab51b-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="ab51b-106">[in] A `ULONG32` boyutunu alır `offsets`, `documents`, `lines`, `columns`, `endLines`, ve `endColumns` dizileri.</span><span class="sxs-lookup"><span data-stu-id="ab51b-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="ab51b-107">[out] Bir işaretçi bir `ULONG32` dizi noktalarını içerecek şekilde gerekli arabellek uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="ab51b-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="ab51b-108">[in] Bir dizi saklanacağı Microsoft Ara dili (MSIL) sıralama noktaları yöntemi başından itibaren kaydırır.</span><span class="sxs-lookup"><span data-stu-id="ab51b-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="ab51b-109">[in] Dizi noktaları bulunan belgeleri depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ab51b-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="ab51b-110">[in] Satırları sıralama noktaları yer olan belgeleri depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ab51b-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="ab51b-111">[in] Sütunları sıralama noktaları yer olan belgeleri depolamak için bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ab51b-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="ab51b-112">[in] Belgelerde dizisi son işaret ettiği satırları dizisi.</span><span class="sxs-lookup"><span data-stu-id="ab51b-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="ab51b-113">[in] Sütun sırası son işaret ettiği belgelerdeki dizisi.</span><span class="sxs-lookup"><span data-stu-id="ab51b-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab51b-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ab51b-114">Return Value</span></span>  
 <span data-ttu-id="ab51b-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ab51b-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab51b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab51b-116">Requirements</span></span>  
 <span data-ttu-id="ab51b-117">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ab51b-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab51b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab51b-118">See also</span></span>
- [<span data-ttu-id="ab51b-119">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab51b-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
