---
title: ISymUnmanagedMethod::GetSequencePointCount Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
ms.openlocfilehash: a44f81deb2d57b49f1fd0650fa52c06383210352
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614441"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="209c8-102">ISymUnmanagedMethod::GetSequencePointCount Metodu</span><span class="sxs-lookup"><span data-stu-id="209c8-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="209c8-103">Bu yöntemin içindeki sıra noktalarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="209c8-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="209c8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="209c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="209c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="209c8-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="209c8-106">dışı `ULONG32`Dizi noktalarını içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="209c8-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="209c8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="209c8-107">Return Value</span></span>  
 <span data-ttu-id="209c8-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="209c8-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="209c8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="209c8-109">Requirements</span></span>  
 <span data-ttu-id="209c8-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="209c8-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="209c8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="209c8-111">See also</span></span>

- [<span data-ttu-id="209c8-112">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="209c8-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
