---
title: ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3343710fbe4f1aba8c38e46a0a720f78944a1c10
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776928"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="06521-102">ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06521-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="06521-103">Sağlama bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="06521-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06521-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06521-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06521-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06521-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="06521-106">[in] Algoritma tanımlayıcısını temsil eden GUID.</span><span class="sxs-lookup"><span data-stu-id="06521-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="06521-107">[in] A `ULONG32` bayt cinsinden boyutunu belirten `checkSum` arabellek.</span><span class="sxs-lookup"><span data-stu-id="06521-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="06521-108">[in] Sağlama toplamı bilgileri depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="06521-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06521-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06521-109">Return Value</span></span>  
 <span data-ttu-id="06521-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="06521-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06521-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06521-111">Requirements</span></span>  
 <span data-ttu-id="06521-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06521-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06521-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06521-113">See also</span></span>

- [<span data-ttu-id="06521-114">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06521-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
