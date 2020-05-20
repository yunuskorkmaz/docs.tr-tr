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
ms.openlocfilehash: a76435be591d9f73d5975c5315f6e744f8972fc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614623"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="1c8bc-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c8bc-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="1c8bc-103">Sağlama toplamı algoritması tanımlayıcısını alır veya hiçbir sağlama toplamı yoksa tüm sıfırları GUID 'leri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c8bc-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c8bc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1c8bc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c8bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c8bc-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1c8bc-106">dışı Sağlama algoritması tanımlayıcısını alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1c8bc-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c8bc-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1c8bc-107">Return Value</span></span>  
 <span data-ttu-id="1c8bc-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="1c8bc-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8bc-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c8bc-109">See also</span></span>

- [<span data-ttu-id="1c8bc-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c8bc-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
