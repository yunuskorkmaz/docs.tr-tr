---
title: ISymUnmanagedMethod::GetSequencePoints Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3cde9de634534acdeafa40bd7a94c46624e49604
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="2746b-102">ISymUnmanagedMethod::GetSequencePoints Metodu</span><span class="sxs-lookup"><span data-stu-id="2746b-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="2746b-103">Bu yöntem içindeki tüm sıralama noktaları alır.</span><span class="sxs-lookup"><span data-stu-id="2746b-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2746b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2746b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="2746b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2746b-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="2746b-106">[in] A `ULONG32` boyutunu alır `offsets`, `documents`, `lines`, `columns`, `endLines`, ve `endColumns` dizileri.</span><span class="sxs-lookup"><span data-stu-id="2746b-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="2746b-107">[out] Bir işaretçi bir `ULONG32` sıralama noktaları içermesi gerekir arabelleği uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="2746b-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="2746b-108">[in] Sıralama noktaları yöntemi başından itibaren dili (MSIL) kaydırır, Microsoft Ara depolamak bir dizi.</span><span class="sxs-lookup"><span data-stu-id="2746b-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="2746b-109">[in] Sıralama noktaları bulunan belgeleri depolamak üzere bir dizi.</span><span class="sxs-lookup"><span data-stu-id="2746b-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="2746b-110">[in] Satırları sıralama noktaları bulunduğu olan belgeleri depolamak üzere bir dizi.</span><span class="sxs-lookup"><span data-stu-id="2746b-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="2746b-111">[in] Sütunları sıralama noktaları bulunduğu olan belgeleri depolamak üzere bir dizi.</span><span class="sxs-lookup"><span data-stu-id="2746b-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="2746b-112">[in] En son sırası işaret belgelerde satırları dizisi.</span><span class="sxs-lookup"><span data-stu-id="2746b-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="2746b-113">[in] En son sırası işaret belgelerde sütun dizisi.</span><span class="sxs-lookup"><span data-stu-id="2746b-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2746b-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2746b-114">Return Value</span></span>  
 <span data-ttu-id="2746b-115">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2746b-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2746b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2746b-116">Requirements</span></span>  
 <span data-ttu-id="2746b-117">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2746b-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2746b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2746b-118">See Also</span></span>  
 [<span data-ttu-id="2746b-119">Isymunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="2746b-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
