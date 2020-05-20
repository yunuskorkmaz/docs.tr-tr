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
ms.openlocfilehash: 06a331e24622e0a155d974ca869818a6532baa1f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615546"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="bdfcb-102">ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdfcb-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="bdfcb-103">Sağlama toplamı bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bdfcb-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdfcb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bdfcb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdfcb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bdfcb-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="bdfcb-106">'ndaki Algoritma tanımlayıcısını temsil eden GUID.</span><span class="sxs-lookup"><span data-stu-id="bdfcb-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="bdfcb-107">'ndaki `ULONG32`Bu, arabelleğin bayt cinsinden boyutunu belirten bir `checkSum` .</span><span class="sxs-lookup"><span data-stu-id="bdfcb-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="bdfcb-108">'ndaki Sağlama toplamı bilgilerini depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="bdfcb-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdfcb-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bdfcb-109">Return Value</span></span>  
 <span data-ttu-id="bdfcb-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bdfcb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdfcb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdfcb-111">Requirements</span></span>  
 <span data-ttu-id="bdfcb-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bdfcb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfcb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdfcb-113">See also</span></span>

- [<span data-ttu-id="bdfcb-114">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bdfcb-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
