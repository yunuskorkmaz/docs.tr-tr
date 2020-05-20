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
ms.openlocfilehash: 25e797fdf563a01ab727f16e7173eec2552eeb27
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614428"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="da785-102">ISymUnmanagedMethod::GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da785-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="da785-103">Bu yöntemin kaynağı için başlangıç ve bitiş belgesi konumlarını alır.</span><span class="sxs-lookup"><span data-stu-id="da785-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="da785-104">İlk dizi konumu başlangıç ' dir ve ikinci dizi konumu son ' dır.</span><span class="sxs-lookup"><span data-stu-id="da785-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da785-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="da785-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da785-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da785-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="da785-107">'ndaki Başlangıç ve bitiş kaynak belgeleri.</span><span class="sxs-lookup"><span data-stu-id="da785-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="da785-108">'ndaki Karşılık gelen kaynak belgelerindeki başlangıç ve bitiş satırları.</span><span class="sxs-lookup"><span data-stu-id="da785-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="da785-109">'ndaki Karşılık gelen kaynak belgelerindeki başlangıç ve bitiş sütunları.</span><span class="sxs-lookup"><span data-stu-id="da785-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="da785-110">[out] `true` pozisyonlar tanımlanmışsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="da785-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da785-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="da785-111">Return Value</span></span>  
 <span data-ttu-id="da785-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="da785-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da785-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da785-113">Requirements</span></span>  
 <span data-ttu-id="da785-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="da785-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da785-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da785-115">See also</span></span>

- [<span data-ttu-id="da785-116">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da785-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
