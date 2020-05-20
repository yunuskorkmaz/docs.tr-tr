---
title: ISymUnmanagedMethod::GetSequencePoints Yöntemi
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
ms.openlocfilehash: 451cfecde7e14fad9d3fed3367112e1fb59796e5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615152"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="c76fb-102">ISymUnmanagedMethod::GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c76fb-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="c76fb-103">Bu yöntemin içindeki tüm sıra noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="c76fb-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c76fb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c76fb-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c76fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c76fb-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="c76fb-106">'ndaki ,,,,, `ULONG32` `offsets` `documents` `lines` `columns` `endLines` Ve `endColumns` dizilerinin boyutunu alan bir.</span><span class="sxs-lookup"><span data-stu-id="c76fb-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="c76fb-107">dışı `ULONG32`Dizi noktalarını içermesi için gereken arabelleğin uzunluğunu alan öğesine bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c76fb-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="c76fb-108">'ndaki Dizi noktaları için yöntemin başlangıcından Microsoft ara dili (MSIL) uzaklıklarını depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="c76fb-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="c76fb-109">'ndaki Dizi noktalarının bulunduğu belgelerin depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="c76fb-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="c76fb-110">'ndaki Sıra noktalarının bulunduğu belgelerde satırların depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="c76fb-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="c76fb-111">'ndaki Dizi noktalarının bulunduğu belgelerde sütunların depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="c76fb-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="c76fb-112">'ndaki Sıra noktalarının sonundaki belgelerdeki satır dizisi.</span><span class="sxs-lookup"><span data-stu-id="c76fb-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="c76fb-113">'ndaki Sıra noktalarının sonundaki belgelerdeki sütunların dizisi.</span><span class="sxs-lookup"><span data-stu-id="c76fb-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c76fb-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c76fb-114">Return Value</span></span>  
 <span data-ttu-id="c76fb-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c76fb-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c76fb-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c76fb-116">Requirements</span></span>  
 <span data-ttu-id="c76fb-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c76fb-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c76fb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c76fb-118">See also</span></span>

- [<span data-ttu-id="c76fb-119">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c76fb-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
