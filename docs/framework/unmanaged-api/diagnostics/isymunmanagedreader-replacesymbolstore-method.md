---
title: ISymUnmanagedReader::ReplaceSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b863816bfb7ed1a5db1fa2234db224b01cb6c9e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481553"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="6a6bd-102">ISymUnmanagedReader::ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a6bd-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="6a6bd-103">Mevcut simge deposu delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="6a6bd-104">Bu yöntem benzer [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) yöntemi dışında verilen delta güncelleştirme yerine tam değiştirme olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a6bd-105">Yalnızca birini belirtmeniz gerekir `filename` veya `pIStream` parametreleri, her ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="6a6bd-106">Varsa `filename` belirtilirse, bu dosyada simgelerle sembol deposundaki güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="6a6bd-107">Varsa `pIStream` belirtilirse, depolama, verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6bd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a6bd-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a6bd-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a6bd-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="6a6bd-110">[in] Sembol deposu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="6a6bd-111">[in] Alternatif olarak kullanılan dosya akışı `filename` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a6bd-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a6bd-112">Return Value</span></span>  
 <span data-ttu-id="6a6bd-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a6bd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a6bd-114">Requirements</span></span>  
 <span data-ttu-id="6a6bd-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a6bd-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6bd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a6bd-116">See also</span></span>
- [<span data-ttu-id="6a6bd-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a6bd-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
