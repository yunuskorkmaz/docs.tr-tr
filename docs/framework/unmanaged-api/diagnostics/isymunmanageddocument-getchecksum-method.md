---
title: ISymUnmanagedDocument::GetCheckSum Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetCheckSum
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 19cd8881bdbd482cb420717855593d7b9583ae51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="00186-102">ISymUnmanagedDocument::GetCheckSum Metodu</span><span class="sxs-lookup"><span data-stu-id="00186-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="00186-103">Sağlama toplamı alır.</span><span class="sxs-lookup"><span data-stu-id="00186-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00186-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00186-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00186-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="00186-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="00186-106">[in] Tarafından sağlanan arabellek uzunluğu `data` parametresi</span><span class="sxs-lookup"><span data-stu-id="00186-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="00186-107">[out] Boyutu ve sağlama toplamı bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="00186-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="00186-108">[out] Sağlama toplamı alan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="00186-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00186-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="00186-109">Return Value</span></span>  
 <span data-ttu-id="00186-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="00186-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00186-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00186-111">See Also</span></span>  
 [<span data-ttu-id="00186-112">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00186-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
