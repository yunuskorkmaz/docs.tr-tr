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
ms.openlocfilehash: f37630c9631e2e76d9b98730b84086b8b86ec55d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427840"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="3d270-102">ISymUnmanagedWriter::RemapToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d270-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="3d270-103">Sembol yazıcı meta verileri yayılan gibi meta veri simgesi eşleştirilmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="3d270-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="3d270-104">Sembol yazan eski belirtecin sembol deposu içinde saklanan istiyorsanız, yeni değer, veya depolanmış belirteciyle okuma aşamasında yeniden eşlemek karşılık gelen simge okuyucu harita kaydetmeniz gerekir ya da güncelleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d270-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d270-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d270-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d270-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d270-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="3d270-107">[in] Eşlendi meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="3d270-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="3d270-108">[in] Hangi yeni meta veri simgesi `oldToken` eşlendi.</span><span class="sxs-lookup"><span data-stu-id="3d270-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d270-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d270-109">Return Value</span></span>  
 <span data-ttu-id="3d270-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3d270-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d270-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d270-111">Requirements</span></span>  
 <span data-ttu-id="3d270-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3d270-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d270-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d270-113">See Also</span></span>  
 [<span data-ttu-id="3d270-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d270-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
