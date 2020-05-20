---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount Metodu
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
ms.openlocfilehash: d096101189d52401c407a4108c9c81e201d3f30d
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441948"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="27932-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Metodu</span><span class="sxs-lookup"><span data-stu-id="27932-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="27932-103">Bu yöntemin içinde satır bulunan belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="27932-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27932-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="27932-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27932-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27932-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="27932-106">dışı `ULONG32`Belgeleri içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="27932-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27932-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="27932-107">Return Value</span></span>  
 <span data-ttu-id="27932-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="27932-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27932-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27932-109">Requirements</span></span>  
 <span data-ttu-id="27932-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="27932-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27932-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27932-111">See also</span></span>

- [<span data-ttu-id="27932-112">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27932-112">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
