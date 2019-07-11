---
title: ISymUnmanagedDocument::HasEmbeddedSource Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 459a24e2ed9b97a67dc0266231fdfc32a9c853a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776654"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="caa07-102">ISymUnmanagedDocument::HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="caa07-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="caa07-103">Döndürür `true` hata ayıklama sembolleri; katıştırılmış kaynak belge varsa, aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="caa07-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="caa07-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caa07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="caa07-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="caa07-106">[out] Belge hata ayıklama sembolleri gömülü kaynak olup olmadığını belirten bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="caa07-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="caa07-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="caa07-107">Return Value</span></span>  
 <span data-ttu-id="caa07-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="caa07-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa07-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="caa07-109">See also</span></span>

- [<span data-ttu-id="caa07-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="caa07-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
