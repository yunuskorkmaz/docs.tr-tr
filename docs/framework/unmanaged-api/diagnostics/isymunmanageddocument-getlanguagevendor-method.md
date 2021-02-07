---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanageddocument:: GetLanguageVendor Yöntemi'
title: ISymUnmanagedDocument::GetLanguageVendor Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
ms.openlocfilehash: 247c6c24f57211b3b46ad773d8e77d7e0f16fd01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710250"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="3d282-103">ISymUnmanagedDocument::GetLanguageVendor Metodu</span><span class="sxs-lookup"><span data-stu-id="3d282-103">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>

<span data-ttu-id="3d282-104">Bu belgenin dil satıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="3d282-104">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d282-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d282-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d282-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d282-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="3d282-107">dışı Dil satıcısını alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d282-107">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d282-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d282-108">Return Value</span></span>  

 <span data-ttu-id="3d282-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="3d282-109">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d282-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d282-110">See also</span></span>

- [<span data-ttu-id="3d282-111">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d282-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
