---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod:: GetSourceStartEnd yöntemi'
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
ms.openlocfilehash: 0d247427998970d86c1ad1ec37f5b32a846a6f7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709990"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="759f3-103">ISymUnmanagedMethod::GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="759f3-103">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>

<span data-ttu-id="759f3-104">Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır.</span><span class="sxs-lookup"><span data-stu-id="759f3-104">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="759f3-105">İlk dizi konumu başlangıç ' dir ve ikinci dizi konumu son ' dır.</span><span class="sxs-lookup"><span data-stu-id="759f3-105">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759f3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="759f3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="759f3-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="759f3-107">Parameters</span></span>  

 `docs`  
 <span data-ttu-id="759f3-108">'ndaki Başlangıç ve bitiş kaynak belgeleri.</span><span class="sxs-lookup"><span data-stu-id="759f3-108">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="759f3-109">'ndaki Karşılık gelen kaynak belgelerindeki başlangıç ve bitiş satırları.</span><span class="sxs-lookup"><span data-stu-id="759f3-109">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="759f3-110">'ndaki Karşılık gelen kaynak belgelerindeki başlangıç ve bitiş sütunları.</span><span class="sxs-lookup"><span data-stu-id="759f3-110">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="759f3-111">[out] `true` pozisyonlar tanımlanmışsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="759f3-111">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="759f3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="759f3-112">Return Value</span></span>  

 <span data-ttu-id="759f3-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="759f3-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="759f3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="759f3-114">Requirements</span></span>  

 <span data-ttu-id="759f3-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="759f3-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="759f3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="759f3-116">See also</span></span>

- [<span data-ttu-id="759f3-117">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="759f3-117">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
