---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: Close yöntemi'
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
ms.openlocfilehash: 02f4d8d4a232240160ad5065947282f40af42f4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762636"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="f8940-103">ISymUnmanagedWriter::Close Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8940-103">ISymUnmanagedWriter::Close Method</span></span>

<span data-ttu-id="f8940-104">Sembolleri sembol deposuna kaydettikten sonra sembol yazıcısını kapatır.</span><span class="sxs-lookup"><span data-stu-id="f8940-104">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8940-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8940-105">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f8940-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f8940-106">Return Value</span></span>  

 <span data-ttu-id="f8940-107">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f8940-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8940-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8940-108">Remarks</span></span>  

 <span data-ttu-id="f8940-109">Bu çağrıdan sonra sembol yazıcısı, daha fazla güncelleştirme için geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f8940-109">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="f8940-110">Sembol yazıcısını sembolleri kaydetmeden kapatmak için, bunun yerine [ıvmunmanagedwriter:: Abort](isymunmanagedwriter-abort-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8940-110">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8940-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8940-111">Requirements</span></span>  

 <span data-ttu-id="f8940-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f8940-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8940-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8940-113">See also</span></span>

- [<span data-ttu-id="f8940-114">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8940-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
