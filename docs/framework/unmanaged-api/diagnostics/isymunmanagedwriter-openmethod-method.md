---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedwriter:: OpenMethod yöntemi'
title: ISymUnmanagedWriter::OpenMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: 2cf7e6bf7c632449c25a2b49c7658fa7b1cc287e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762233"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="683e6-103">ISymUnmanagedWriter::OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="683e6-103">ISymUnmanagedWriter::OpenMethod Method</span></span>

<span data-ttu-id="683e6-104">Sembol bilgisinin yayıldığını bir yöntem açar.</span><span class="sxs-lookup"><span data-stu-id="683e6-104">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="683e6-105">Verilen yöntem, dizi noktalarını, parametreleri ve sözcük temelli kapsamları tanımlamak için çağrılar için geçerli yöntem haline gelir.</span><span class="sxs-lookup"><span data-stu-id="683e6-105">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="683e6-106">Tüm yöntem etrafında örtük bir sözcük temelli kapsam vardır.</span><span class="sxs-lookup"><span data-stu-id="683e6-106">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="683e6-107">Daha önce kapatılan bir yöntemi yeniden açmak, bu yöntem için önceden tanımlanmış tüm sembolleri siler.</span><span class="sxs-lookup"><span data-stu-id="683e6-107">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="683e6-108">Tek seferde yalnızca bir açık yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="683e6-108">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="683e6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="683e6-109">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="683e6-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="683e6-110">Parameters</span></span>  

 `method`  
 <span data-ttu-id="683e6-111">'ndaki Açılacak yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="683e6-111">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="683e6-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="683e6-112">Return Value</span></span>  

 <span data-ttu-id="683e6-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="683e6-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="683e6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="683e6-114">Requirements</span></span>  

 <span data-ttu-id="683e6-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="683e6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683e6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="683e6-116">See also</span></span>

- [<span data-ttu-id="683e6-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="683e6-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="683e6-118">CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="683e6-118">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="683e6-119">OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="683e6-119">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)
