---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanageddocument:: HasEmbeddedSource Yöntemi'
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
ms.openlocfilehash: fcab83fea65d9a9e483bff9d2d75714c233718eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710133"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="8e7ff-103">ISymUnmanagedDocument::HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e7ff-103">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>

<span data-ttu-id="8e7ff-104">`true`Belgenin hata ayıklama sembollerine katıştırılmış kaynak olup olmadığını döndürür; Aksi takdirde, döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="8e7ff-104">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e7ff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e7ff-105">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e7ff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e7ff-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8e7ff-107">dışı Belgenin hata ayıklama sembollerine gömülü kaynak olup olmadığını gösteren bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8e7ff-107">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e7ff-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e7ff-108">Return Value</span></span>  

 <span data-ttu-id="8e7ff-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="8e7ff-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e7ff-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e7ff-110">See also</span></span>

- [<span data-ttu-id="8e7ff-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e7ff-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
