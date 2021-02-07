---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetMethodVersion yöntemi'
title: ISymUnmanagedReader::GetMethodVersion Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: 027f65f858aab3e4ad0bc0bfbffd91f6118b80b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764027"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="fde8c-103">ISymUnmanagedReader::GetMethodVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="fde8c-103">ISymUnmanagedReader::GetMethodVersion Method</span></span>

<span data-ttu-id="fde8c-104">Yöntem sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="fde8c-104">Gets the method version.</span></span> <span data-ttu-id="fde8c-105">Yöntem sürümü 1 ' de başlar ve yöntemin her yeniden derlenmesi sırasında artırılır.</span><span class="sxs-lookup"><span data-stu-id="fde8c-105">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="fde8c-106">Yeniden derleme, yöntemde değişiklik yapılmadan meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="fde8c-106">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fde8c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fde8c-107">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fde8c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fde8c-108">Parameters</span></span>  

 `pMethod`  
 <span data-ttu-id="fde8c-109">'ndaki Sürümünün alınacağı yöntem.</span><span class="sxs-lookup"><span data-stu-id="fde8c-109">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="fde8c-110">dışı Yöntem sürümünü alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fde8c-110">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fde8c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fde8c-111">Return Value</span></span>  

 <span data-ttu-id="fde8c-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fde8c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fde8c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fde8c-113">Requirements</span></span>  

 <span data-ttu-id="fde8c-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fde8c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde8c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fde8c-115">See also</span></span>

- [<span data-ttu-id="fde8c-116">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fde8c-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
