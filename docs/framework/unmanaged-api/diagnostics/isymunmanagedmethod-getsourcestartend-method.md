---
title: ISymUnmanagedMethod::GetSourceStartEnd Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: f53afa5f87f1502f287b25e3d9756f9a54ad6869
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699293"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="45b3b-102">ISymUnmanagedMethod::GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45b3b-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>

<span data-ttu-id="45b3b-103">Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır.</span><span class="sxs-lookup"><span data-stu-id="45b3b-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="45b3b-104">İlk dizi konumu başlangıç ' dir ve ikinci dizi konumu son ' dır.</span><span class="sxs-lookup"><span data-stu-id="45b3b-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45b3b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="45b3b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45b3b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45b3b-106">Parameters</span></span>  

 `docs`  
 <span data-ttu-id="45b3b-107">'ndaki Başlangıç ve bitiş kaynak belgeleri.</span><span class="sxs-lookup"><span data-stu-id="45b3b-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="45b3b-108">'ndaki Karşılık gelen kaynak belgelerindeki başlangıç ve bitiş satırları.</span><span class="sxs-lookup"><span data-stu-id="45b3b-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="45b3b-109">'ndaki Karşılık gelen kaynak belgelerindeki başlangıç ve bitiş sütunları.</span><span class="sxs-lookup"><span data-stu-id="45b3b-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="45b3b-110">[out] `true` pozisyonlar tanımlanmışsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="45b3b-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45b3b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="45b3b-111">Return Value</span></span>  

 <span data-ttu-id="45b3b-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="45b3b-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45b3b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45b3b-113">Requirements</span></span>  

 <span data-ttu-id="45b3b-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="45b3b-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b3b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45b3b-115">See also</span></span>

- [<span data-ttu-id="45b3b-116">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45b3b-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
