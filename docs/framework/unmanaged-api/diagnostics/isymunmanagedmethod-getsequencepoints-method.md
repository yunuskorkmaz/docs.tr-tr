---
description: 'Şu konuda daha fazla bilgi edinin: ırivınunmanagedmethod:: GetSequencePoints yöntemi'
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
ms.openlocfilehash: acdfcb014648593065bd1ae252ef936898a1e8b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721300"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="71f57-103">ISymUnmanagedMethod::GetSequencePoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71f57-103">ISymUnmanagedMethod::GetSequencePoints Method</span></span>

<span data-ttu-id="71f57-104">Bu yöntemin içindeki tüm sıra noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="71f57-104">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f57-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71f57-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="71f57-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71f57-106">Parameters</span></span>  

 `cPoints`  
 <span data-ttu-id="71f57-107">'ndaki ,,,,, `ULONG32` `offsets` `documents` `lines` `columns` `endLines` Ve `endColumns` dizilerinin boyutunu alan bir.</span><span class="sxs-lookup"><span data-stu-id="71f57-107">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="71f57-108">dışı `ULONG32` Dizi noktalarını içermesi için gereken arabelleğin uzunluğunu alan öğesine bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="71f57-108">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="71f57-109">'ndaki Dizi noktaları için yöntemin başlangıcından Microsoft ara dili (MSIL) uzaklıklarını depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="71f57-109">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="71f57-110">'ndaki Dizi noktalarının bulunduğu belgelerin depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="71f57-110">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="71f57-111">'ndaki Sıra noktalarının bulunduğu belgelerde satırların depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="71f57-111">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="71f57-112">'ndaki Dizi noktalarının bulunduğu belgelerde sütunların depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="71f57-112">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="71f57-113">'ndaki Sıra noktalarının sonundaki belgelerdeki satır dizisi.</span><span class="sxs-lookup"><span data-stu-id="71f57-113">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="71f57-114">'ndaki Sıra noktalarının sonundaki belgelerdeki sütunların dizisi.</span><span class="sxs-lookup"><span data-stu-id="71f57-114">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71f57-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="71f57-115">Return Value</span></span>  

 <span data-ttu-id="71f57-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="71f57-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71f57-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71f57-117">Requirements</span></span>  

 <span data-ttu-id="71f57-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="71f57-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f57-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71f57-119">See also</span></span>

- [<span data-ttu-id="71f57-120">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71f57-120">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
