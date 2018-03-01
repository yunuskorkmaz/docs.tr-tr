---
title: "ISymUnmanagedWriter::RemapToken Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86d6c78a49c55bdc9093241952bee00ee331696e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="a271b-102">ISymUnmanagedWriter::RemapToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a271b-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="a271b-103">Sembol yazıcı meta verileri yayılan gibi meta veri simgesi eşleştirilmiş bildirir.</span><span class="sxs-lookup"><span data-stu-id="a271b-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="a271b-104">Sembol yazan eski belirtecin sembol deposu içinde saklanan istiyorsanız, yeni değer, veya depolanmış belirteciyle okuma aşamasında yeniden eşlemek karşılık gelen simge okuyucu harita kaydetmeniz gerekir ya da güncelleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="a271b-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a271b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a271b-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a271b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a271b-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="a271b-107">[in] Eşlendi meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="a271b-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="a271b-108">[in] Hangi yeni meta veri simgesi `oldToken` eşlendi.</span><span class="sxs-lookup"><span data-stu-id="a271b-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a271b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a271b-109">Return Value</span></span>  
 <span data-ttu-id="a271b-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a271b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a271b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a271b-111">Requirements</span></span>  
 <span data-ttu-id="a271b-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a271b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a271b-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a271b-113">See Also</span></span>  
 [<span data-ttu-id="a271b-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a271b-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
