---
title: ISymUnmanagedWriter::Close Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
ms.openlocfilehash: 1d684c14f14fcc93040798ae4ee3b8bb1df5354d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733262"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="b3c38-102">ISymUnmanagedWriter::Close Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3c38-102">ISymUnmanagedWriter::Close Method</span></span>

<span data-ttu-id="b3c38-103">Sembolleri sembol deposuna kaydettikten sonra sembol yazıcısını kapatır.</span><span class="sxs-lookup"><span data-stu-id="b3c38-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c38-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b3c38-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b3c38-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b3c38-105">Return Value</span></span>  

 <span data-ttu-id="b3c38-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b3c38-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3c38-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3c38-107">Remarks</span></span>  

 <span data-ttu-id="b3c38-108">Bu çağrıdan sonra sembol yazıcısı, daha fazla güncelleştirme için geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="b3c38-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="b3c38-109">Sembol yazıcısını sembolleri kaydetmeden kapatmak için, bunun yerine [ıvmunmanagedwriter:: Abort](isymunmanagedwriter-abort-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3c38-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3c38-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3c38-110">Requirements</span></span>  

 <span data-ttu-id="b3c38-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b3c38-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c38-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3c38-112">See also</span></span>

- [<span data-ttu-id="b3c38-113">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3c38-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
