---
title: ISymUnmanagedDocument::GetSourceLength Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
ms.openlocfilehash: 0551e8b4f381f76e7bbac06ca7b5f6aea5bbb61f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449157"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="4c1ab-102">ISymUnmanagedDocument::GetSourceLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c1ab-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="4c1ab-103">Gets the length, in bytes, of the embedded source.</span><span class="sxs-lookup"><span data-stu-id="4c1ab-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c1ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c1ab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c1ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c1ab-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4c1ab-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span><span class="sxs-lookup"><span data-stu-id="4c1ab-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c1ab-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4c1ab-107">Return Value</span></span>  
 <span data-ttu-id="4c1ab-108">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="4c1ab-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c1ab-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c1ab-109">See also</span></span>

- [<span data-ttu-id="4c1ab-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c1ab-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
