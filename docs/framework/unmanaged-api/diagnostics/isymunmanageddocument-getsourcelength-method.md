---
title: ISymUnmanagedDocument::GetSourceLength Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edafb60e5b6f9b913e89f4785dc34a58bf390f2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638775"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="69a53-102">ISymUnmanagedDocument::GetSourceLength Metodu</span><span class="sxs-lookup"><span data-stu-id="69a53-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="69a53-103">Katıştırılmış kaynak bayt cinsinden uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="69a53-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69a53-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69a53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69a53-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="69a53-106">[out] Uzunluğu, bayt cinsinden katıştırılmış kaynak gösteren bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="69a53-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69a53-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69a53-107">Return Value</span></span>  
 <span data-ttu-id="69a53-108">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="69a53-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a53-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69a53-109">See also</span></span>
- [<span data-ttu-id="69a53-110">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69a53-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
