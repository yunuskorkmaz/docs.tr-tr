---
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
ms.openlocfilehash: fcf250f10baf4c65cd1c8c918655e4b9f4f5cc4b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731741"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="7579b-102">ISymUnmanagedWriter::CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7579b-102">ISymUnmanagedWriter::CloseMethod Method</span></span>

<span data-ttu-id="7579b-103">Geçerli yöntemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="7579b-103">Closes the current method.</span></span> <span data-ttu-id="7579b-104">Bir yöntem kapatıldıktan sonra bunun içinde başka semboller tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="7579b-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7579b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7579b-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7579b-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7579b-106">Return Value</span></span>  

 <span data-ttu-id="7579b-107">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7579b-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7579b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7579b-108">Requirements</span></span>  

 <span data-ttu-id="7579b-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7579b-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7579b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7579b-110">See also</span></span>

- [<span data-ttu-id="7579b-111">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7579b-111">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="7579b-112">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7579b-112">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
