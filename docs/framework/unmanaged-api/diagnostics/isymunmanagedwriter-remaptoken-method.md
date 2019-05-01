---
title: ISymUnmanagedWriter::RemapToken Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 979d14b4c404c3bf12c427bd5b8b1d4997805e7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986017"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="7618f-102">ISymUnmanagedWriter::RemapToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7618f-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="7618f-103">Sembol yazıcı meta veriler gösteriliyordu gibi meta veri belirteci eşleştirilmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="7618f-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="7618f-104">Sembol yazıcı, sembol deposundaki eski belirteç saklanan güncelleştirmek ya da yeni bir değer veya saklı belirteciyle okuma aşamasında yeniden eşlemek karşılık gelen sembol Okuyucu için haritada kaydetmelisiniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7618f-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7618f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7618f-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7618f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7618f-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="7618f-107">[in] Eşlendi meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="7618f-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="7618f-108">[in] Hangi yeni meta veri belirteci `oldToken` eşlendi.</span><span class="sxs-lookup"><span data-stu-id="7618f-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7618f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7618f-109">Return Value</span></span>  
 <span data-ttu-id="7618f-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7618f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7618f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7618f-111">Requirements</span></span>  
 <span data-ttu-id="7618f-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7618f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7618f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7618f-113">See also</span></span>

- [<span data-ttu-id="7618f-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7618f-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
