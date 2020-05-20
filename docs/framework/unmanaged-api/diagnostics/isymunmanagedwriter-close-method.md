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
ms.openlocfilehash: 0a7ecd475a8031fedb2c8474593b45045fcc6fb9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610138"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="68870-102">ISymUnmanagedWriter::Close Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68870-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="68870-103">Sembolleri sembol deposuna kaydettikten sonra sembol yazıcısını kapatır.</span><span class="sxs-lookup"><span data-stu-id="68870-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68870-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="68870-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="68870-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68870-105">Return Value</span></span>  
 <span data-ttu-id="68870-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="68870-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68870-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68870-107">Remarks</span></span>  
 <span data-ttu-id="68870-108">Bu çağrıdan sonra sembol yazıcısı, daha fazla güncelleştirme için geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="68870-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="68870-109">Sembol yazıcısını sembolleri kaydetmeden kapatmak için, bunun yerine [ıvmunmanagedwriter:: Abort](isymunmanagedwriter-abort-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="68870-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68870-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68870-110">Requirements</span></span>  
 <span data-ttu-id="68870-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="68870-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68870-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68870-112">See also</span></span>

- [<span data-ttu-id="68870-113">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68870-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
