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
ms.openlocfilehash: d654f6d57bd784063fc7f87dd9767bdc27ad2776
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615585"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="c7e72-102">ISymUnmanagedDocument::HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7e72-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="c7e72-103">`true`Belgenin hata ayıklama sembollerine katıştırılmış kaynak olup olmadığını döndürür; Aksi takdirde, döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="c7e72-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e72-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c7e72-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7e72-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7e72-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c7e72-106">dışı Belgenin hata ayıklama sembollerine gömülü kaynak olup olmadığını gösteren bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7e72-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7e72-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7e72-107">Return Value</span></span>  
 <span data-ttu-id="c7e72-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="c7e72-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e72-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7e72-109">See also</span></span>

- [<span data-ttu-id="c7e72-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7e72-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
