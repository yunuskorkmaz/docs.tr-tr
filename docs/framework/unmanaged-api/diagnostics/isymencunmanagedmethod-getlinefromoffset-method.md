---
description: 'Şu konuda daha fazla bilgi edinin: ıvmencunmanagedmethod:: Getlinefromsapmayı yöntemi'
title: ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 18fe942b509340c89a4c3044e02bf8e9d952f91d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737967"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="88a44-103">ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88a44-103">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>

<span data-ttu-id="88a44-104">Bir uzaklığa ilişkin satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="88a44-104">Gets the line information associated with an offset.</span></span> <span data-ttu-id="88a44-105">Eğer fark parametresi ( `dwOffset` ) bir sıra noktası değilse, bu yöntem önceki uzaklığa ilişkin satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="88a44-105">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a44-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88a44-106">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88a44-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88a44-107">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="88a44-108">'ndaki `ULONG32` Bu, sapmayı içeren bir.</span><span class="sxs-lookup"><span data-stu-id="88a44-108">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="88a44-109">dışı Satırı alan bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="88a44-109">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="88a44-110">dışı Sütununu alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="88a44-110">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="88a44-111">dışı `ULONG32` Bitiş satırını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="88a44-111">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="88a44-112">dışı Bitiş sütununu alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="88a44-112">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="88a44-113">dışı `ULONG32` İlişkili dizi noktasını alan öğesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88a44-113">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88a44-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="88a44-114">Return Value</span></span>  

 <span data-ttu-id="88a44-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="88a44-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a44-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88a44-116">Requirements</span></span>  

 <span data-ttu-id="88a44-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="88a44-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a44-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88a44-118">See also</span></span>

- [<span data-ttu-id="88a44-119">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88a44-119">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
