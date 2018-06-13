---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c815b256ebdab82a57f921a5df016a1552f6d052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424358"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="82609-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Metodu</span><span class="sxs-lookup"><span data-stu-id="82609-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="82609-103">Sağlama toplamı algoritması tanımlayıcısını alır veya hiçbir sağlama toplamı ise sıfırlardan GUİD'si döndürür.</span><span class="sxs-lookup"><span data-stu-id="82609-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82609-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82609-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82609-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82609-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="82609-106">[out] Bir işaretçi bir değişkene sağlama toplamı algoritması tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="82609-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82609-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="82609-107">Return Value</span></span>  
 <span data-ttu-id="82609-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="82609-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82609-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82609-109">See Also</span></span>  
 [<span data-ttu-id="82609-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82609-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
