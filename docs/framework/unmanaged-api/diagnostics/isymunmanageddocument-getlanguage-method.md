---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanageddocument:: GetLanguage yöntemi'
title: ISymUnmanagedDocument::GetLanguage Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: f30636303d310ed91aa4229f52a3197a29190d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710315"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="e1c27-103">ISymUnmanagedDocument::GetLanguage Metodu</span><span class="sxs-lookup"><span data-stu-id="e1c27-103">ISymUnmanagedDocument::GetLanguage Method</span></span>

<span data-ttu-id="e1c27-104">Bu belgenin dil tanımlayıcısını alır</span><span class="sxs-lookup"><span data-stu-id="e1c27-104">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1c27-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c27-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1c27-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="e1c27-107">dışı Dil tanımlayıcısını alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e1c27-107">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1c27-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e1c27-108">Return Value</span></span>  

 <span data-ttu-id="e1c27-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="e1c27-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c27-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1c27-110">See also</span></span>

- [<span data-ttu-id="e1c27-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1c27-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
