---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: 2bc673d2e331cd32d5317cb20f9418eb3a3b144a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431070"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="6e4a6-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e4a6-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="6e4a6-103">Sağlama toplamı algoritması tanımlayıcısını alır veya hiçbir sağlama toplamı yoksa tüm sıfırları GUID 'leri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e4a6-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e4a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e4a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e4a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e4a6-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6e4a6-106">dışı Sağlama algoritması tanımlayıcısını alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e4a6-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e4a6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6e4a6-107">Return Value</span></span>  
 <span data-ttu-id="6e4a6-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="6e4a6-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4a6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e4a6-109">See also</span></span>

- [<span data-ttu-id="6e4a6-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e4a6-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
