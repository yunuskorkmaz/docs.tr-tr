---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedwriter:: RemapToken Yöntemi'
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
ms.openlocfilehash: c065d42c3d2749f0262fdd81a74de918274ba67d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762090"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="5a262-103">ISymUnmanagedWriter::RemapToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a262-103">ISymUnmanagedWriter::RemapToken Method</span></span>

<span data-ttu-id="5a262-104">Meta veri yayıldığından, meta veri belirtecinin yeniden eşlenme olduğunu sembol yazıcısına bildirir.</span><span class="sxs-lookup"><span data-stu-id="5a262-104">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="5a262-105">Sembol yazıcısı eski belirteci sembol deposu içinde depolamışsa, bu, saklı belirteci yeni değerle güncelleştirmeli ya da okuma aşamasında yeniden eşlemek üzere ilgili sembol okuyucusunun eşlemesini kaydetmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a262-105">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a262-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a262-106">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a262-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a262-107">Parameters</span></span>  

 `oldToken`  
 <span data-ttu-id="5a262-108">'ndaki Yeniden eşlenen meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="5a262-108">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="5a262-109">'ndaki Yeniden eşlenen yeni meta veri belirteci `oldToken` .</span><span class="sxs-lookup"><span data-stu-id="5a262-109">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a262-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a262-110">Return Value</span></span>  

 <span data-ttu-id="5a262-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5a262-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a262-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a262-112">Requirements</span></span>  

 <span data-ttu-id="5a262-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5a262-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a262-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a262-114">See also</span></span>

- [<span data-ttu-id="5a262-115">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a262-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
