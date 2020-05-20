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
ms.openlocfilehash: 543bd208e5492460435663c32f276472a763f613
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441103"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="b1bbd-102">ISymUnmanagedDocument::GetCheckSum Metodu</span><span class="sxs-lookup"><span data-stu-id="b1bbd-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>
<span data-ttu-id="b1bbd-103">Sağlama toplamını alır.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bbd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b1bbd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1bbd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1bbd-105">Parameters</span></span>  
 `cData`  
 <span data-ttu-id="b1bbd-106">'ndaki Parametre tarafından belirtilen arabelleğin uzunluğu `data`</span><span class="sxs-lookup"><span data-stu-id="b1bbd-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="b1bbd-107">dışı Sağlama toplamı için bayt cinsinden boyut ve uzunluk.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="b1bbd-108">dışı Sağlama toplamını alan arabellek.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1bbd-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1bbd-109">Return Value</span></span>  
 <span data-ttu-id="b1bbd-110">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bbd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-111">See also</span></span>

- [<span data-ttu-id="b1bbd-112">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1bbd-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
