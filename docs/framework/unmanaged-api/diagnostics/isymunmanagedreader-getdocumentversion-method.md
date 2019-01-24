---
title: ISymUnmanagedReader::GetDocumentVersion Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf6a08b17819e3d3cdaa62b0e209fc2064de4a4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688707"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="1fc4d-102">ISymUnmanagedReader::GetDocumentVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="1fc4d-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="1fc4d-103">Belirtilen belge belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="1fc4d-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="1fc4d-104">Belge sürüm 1'den başlar ve her zaman belge kullanılarak güncelleştirilir artırılır [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1fc4d-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="1fc4d-105">Varsa `pbCurrent` parametresi `true`, bu belgenin en son sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="1fc4d-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc4d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1fc4d-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fc4d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1fc4d-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="1fc4d-108">[in] Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="1fc4d-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="1fc4d-109">[out] Belirtilen belge sürümünü alır bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1fc4d-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="1fc4d-110">[out] Bir işaretçi alır bir değişkene `true` bu belgenin en son sürüm ise veya `false` en son sürümü Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="1fc4d-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fc4d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1fc4d-111">Return Value</span></span>  
 <span data-ttu-id="1fc4d-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1fc4d-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fc4d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fc4d-113">Requirements</span></span>  
 <span data-ttu-id="1fc4d-114">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1fc4d-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc4d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fc4d-115">See also</span></span>
- [<span data-ttu-id="1fc4d-116">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1fc4d-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
