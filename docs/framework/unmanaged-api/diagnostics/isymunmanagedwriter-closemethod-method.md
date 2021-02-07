---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedwriter:: CloseMethod yöntemi'
title: ISymUnmanagedWriter::CloseMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
ms.openlocfilehash: 8d19de0827f94d52c92852b0d1f2b5567e109c15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762584"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="01db9-103">ISymUnmanagedWriter::CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01db9-103">ISymUnmanagedWriter::CloseMethod Method</span></span>

<span data-ttu-id="01db9-104">Geçerli yöntemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="01db9-104">Closes the current method.</span></span> <span data-ttu-id="01db9-105">Bir yöntem kapatıldıktan sonra bunun içinde başka semboller tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="01db9-105">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01db9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="01db9-106">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="01db9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="01db9-107">Return Value</span></span>  

 <span data-ttu-id="01db9-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="01db9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01db9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01db9-109">Requirements</span></span>  

 <span data-ttu-id="01db9-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="01db9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01db9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01db9-111">See also</span></span>

- [<span data-ttu-id="01db9-112">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01db9-112">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="01db9-113">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01db9-113">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
