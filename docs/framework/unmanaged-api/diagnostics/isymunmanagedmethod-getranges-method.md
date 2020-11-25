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
ms.openlocfilehash: 8ed492b573215736c82ab6c231cc5f2e188ea013
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732157"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="a7b5a-102">ISymUnmanagedMethod::GetRanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7b5a-102">ISymUnmanagedMethod::GetRanges Method</span></span>

<span data-ttu-id="a7b5a-103">Belgedeki bir konum verildiğinde, konumun bu yöntem içinde kapsamakta olduğu Microsoft ara dili (MSIL) aralıklarına karşılık gelen başlangıç ve bitiş konumu çiftleri dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="a7b5a-104">Dizi tamsayılar dizisidir ve [Start, End, Start, End] biçiminde olur.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="a7b5a-105">Aralık çifti sayısı, dizinin uzunluğu 2 ' ye bölünür.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b5a-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a7b5a-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a7b5a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7b5a-107">Parameters</span></span>  

 `document`  
 <span data-ttu-id="a7b5a-108">'ndaki Kaydırın istendiği belge.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="a7b5a-109">'ndaki Aralıklara karşılık gelen belge satırı.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="a7b5a-110">'ndaki Aralıklara karşılık gelen belge sütunu.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="a7b5a-111">'ndaki `ranges` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="a7b5a-112">dışı `ULONG32` Aralıkları içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="a7b5a-113">dışı Aralıkları alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7b5a-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7b5a-114">Return Value</span></span>  

 <span data-ttu-id="a7b5a-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b5a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7b5a-116">Requirements</span></span>  

 <span data-ttu-id="a7b5a-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a7b5a-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b5a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7b5a-118">See also</span></span>

- [<span data-ttu-id="a7b5a-119">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7b5a-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
