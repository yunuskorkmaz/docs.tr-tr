---
title: "ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocumentWriter.SetCheckSum
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9693b21c2b3819096ec4aeb0a275fccf76307de0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="61497-102">ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61497-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="61497-103">Sağlama bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="61497-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61497-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61497-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61497-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61497-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="61497-106">[in] Algoritma tanımlayıcısı temsil eden GUID.</span><span class="sxs-lookup"><span data-stu-id="61497-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="61497-107">[in] A `ULONG32` bayt cinsinden boyutu belirten `checkSum` arabellek.</span><span class="sxs-lookup"><span data-stu-id="61497-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="61497-108">[in] Sağlama bilgilerini depolayan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="61497-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61497-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61497-109">Return Value</span></span>  
 <span data-ttu-id="61497-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="61497-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61497-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61497-111">Requirements</span></span>  
 <span data-ttu-id="61497-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="61497-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61497-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61497-113">See Also</span></span>  
 [<span data-ttu-id="61497-114">Isymunmanageddocumentwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="61497-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
