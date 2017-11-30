---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 268951d70fec1096fc9cafaeeb6da3b83bc0acf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="77f33-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Metodu</span><span class="sxs-lookup"><span data-stu-id="77f33-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="77f33-103">Sağlama toplamı algoritması tanımlayıcısını alır veya hiçbir sağlama toplamı ise sıfırlardan GUİD'si döndürür.</span><span class="sxs-lookup"><span data-stu-id="77f33-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77f33-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77f33-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77f33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77f33-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="77f33-106">[out] Bir işaretçi bir değişkene sağlama toplamı algoritması tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="77f33-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77f33-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77f33-107">Return Value</span></span>  
 <span data-ttu-id="77f33-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="77f33-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f33-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77f33-109">See Also</span></span>  
 [<span data-ttu-id="77f33-110">Isymunmanageddocument arabirimi</span><span class="sxs-lookup"><span data-stu-id="77f33-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
