---
title: ISymUnmanagedDocument::GetCheckSum Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80cda4c31ca78e0350639df809ec1e9f1dcbbaea
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498256"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="1ca56-102">ISymUnmanagedDocument::GetCheckSum Metodu</span><span class="sxs-lookup"><span data-stu-id="1ca56-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="1ca56-103">Sağlama toplamı alır.</span><span class="sxs-lookup"><span data-stu-id="1ca56-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ca56-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ca56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ca56-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="1ca56-106">[in] Tarafından sağlanan arabellek uzunluğu `data` parametresi</span><span class="sxs-lookup"><span data-stu-id="1ca56-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="1ca56-107">[out] Boyutu ve sağlama toplamı bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1ca56-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="1ca56-108">[out] Sağlama toplamı alan arabellek.</span><span class="sxs-lookup"><span data-stu-id="1ca56-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ca56-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1ca56-109">Return Value</span></span>  
 <span data-ttu-id="1ca56-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1ca56-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca56-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ca56-111">See also</span></span>
- [<span data-ttu-id="1ca56-112">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ca56-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
