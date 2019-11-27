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
ms.openlocfilehash: 057b901337ded7b5336ef673624d8d6c827c8932
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448674"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="cfa53-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Metodu</span><span class="sxs-lookup"><span data-stu-id="cfa53-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="cfa53-103">Bu yöntemin içinde satır bulunan belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cfa53-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfa53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfa53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfa53-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="cfa53-106">dışı Belgeleri içermesi için gereken arabelleğin boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cfa53-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfa53-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cfa53-107">Return Value</span></span>  
 <span data-ttu-id="cfa53-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cfa53-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa53-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfa53-109">Requirements</span></span>  
 <span data-ttu-id="cfa53-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cfa53-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa53-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfa53-111">See also</span></span>

- [<span data-ttu-id="cfa53-112">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa53-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
