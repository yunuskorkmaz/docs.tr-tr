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
ms.openlocfilehash: c2cc541b2a78f16d5ca6b19405794faa825a9d72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615039"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="5ee0e-102">ISymUnmanagedReader::GetDocumentVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="5ee0e-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="5ee0e-103">Belirtilen belgenin belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="5ee0e-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="5ee0e-104">Belge sürümü 1 ' de başlar ve belge [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) yöntemi kullanılarak her güncelleştirildiği zaman artırılır.</span><span class="sxs-lookup"><span data-stu-id="5ee0e-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="5ee0e-105">`pbCurrent`Parametresi ise `true` , bu belgenin en son sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="5ee0e-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee0e-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5ee0e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ee0e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ee0e-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="5ee0e-108">'ndaki Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="5ee0e-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="5ee0e-109">dışı Belirtilen belgenin sürümünü alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ee0e-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="5ee0e-110">dışı `true`Belgenin en son sürümü ise veya `false` en son sürüm değilse alan bir değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ee0e-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ee0e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5ee0e-111">Return Value</span></span>  
 <span data-ttu-id="5ee0e-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5ee0e-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee0e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ee0e-113">Requirements</span></span>  
 <span data-ttu-id="5ee0e-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5ee0e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee0e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ee0e-115">See also</span></span>

- [<span data-ttu-id="5ee0e-116">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ee0e-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
