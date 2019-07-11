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
ms.openlocfilehash: c04ca1d56f3e93c77f335218bb534f890e9053d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776615"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="4245b-102">ISymUnmanagedWriter::RemapToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4245b-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="4245b-103">Sembol yazıcı meta veriler gösteriliyordu gibi meta veri belirteci eşleştirilmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="4245b-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="4245b-104">Sembol yazıcı, sembol deposundaki eski belirteç saklanan güncelleştirmek ya da yeni bir değer veya saklı belirteciyle okuma aşamasında yeniden eşlemek karşılık gelen sembol Okuyucu için haritada kaydetmelisiniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4245b-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4245b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4245b-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4245b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4245b-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="4245b-107">[in] Eşlendi meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4245b-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="4245b-108">[in] Hangi yeni meta veri belirteci `oldToken` eşlendi.</span><span class="sxs-lookup"><span data-stu-id="4245b-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4245b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4245b-109">Return Value</span></span>  
 <span data-ttu-id="4245b-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4245b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4245b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4245b-111">Requirements</span></span>  
 <span data-ttu-id="4245b-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4245b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4245b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4245b-113">See also</span></span>

- [<span data-ttu-id="4245b-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4245b-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
