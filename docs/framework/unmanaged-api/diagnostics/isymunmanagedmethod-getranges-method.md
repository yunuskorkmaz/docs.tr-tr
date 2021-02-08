---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod:: GetRanges yöntemi'
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
ms.openlocfilehash: e6a1da285c0574ef5910e8e727c3bcc5cb9e5d35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790106"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="e3976-103">ISymUnmanagedMethod::GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3976-103">ISymUnmanagedMethod::GetRanges Method</span></span>

<span data-ttu-id="e3976-104">Belgedeki bir konum verildiğinde, konumun bu yöntem içinde kapsamakta olduğu Microsoft ara dili (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş konumu çiftleri dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e3976-104">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="e3976-105">Dizi tamsayılar dizisidir ve [Start, End, Start, End] biçiminde olur.</span><span class="sxs-lookup"><span data-stu-id="e3976-105">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="e3976-106">Aralık çifti sayısı, dizinin uzunluğu 2 ' ye bölünür.</span><span class="sxs-lookup"><span data-stu-id="e3976-106">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3976-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3976-107">Syntax</span></span>  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3976-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3976-108">Parameters</span></span>  

 `document`  
 <span data-ttu-id="e3976-109">'ndaki Kaydırın istendiği belge.</span><span class="sxs-lookup"><span data-stu-id="e3976-109">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="e3976-110">'ndaki Aralıklara karşılık gelen belge satırı.</span><span class="sxs-lookup"><span data-stu-id="e3976-110">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="e3976-111">'ndaki Aralıklara karşılık gelen belge sütunu.</span><span class="sxs-lookup"><span data-stu-id="e3976-111">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="e3976-112">'ndaki `ranges` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e3976-112">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="e3976-113">dışı `ULONG32` Aralıkları içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e3976-113">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="e3976-114">dışı Aralıkları alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e3976-114">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3976-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e3976-115">Return Value</span></span>  

 <span data-ttu-id="e3976-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e3976-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3976-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3976-117">Requirements</span></span>  

 <span data-ttu-id="e3976-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e3976-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3976-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3976-119">See also</span></span>

- [<span data-ttu-id="e3976-120">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3976-120">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
