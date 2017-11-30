---
title: "ISymUnmanagedReader::ReplaceSymbolStore Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.ReplaceSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09bcad4898cf4d3310a96164bdc82006e185006f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="67888-102">ISymUnmanagedReader::ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67888-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="67888-103">Varolan sembol deposu delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="67888-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="67888-104">Bu yöntem benzer [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) yöntemi, bir güncelleştirme yerine tam değiştirme olarak verilen delta davranır ancak bu.</span><span class="sxs-lookup"><span data-stu-id="67888-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67888-105">Yalnızca birini belirtmeniz `filename` veya `pIStream` parametreleri, her ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="67888-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="67888-106">Varsa `filename` belirtilirse, bu dosyada simgelerle sembol deposu güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="67888-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="67888-107">Varsa `pIStream` belirtilirse, depolama, verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="67888-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67888-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67888-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67888-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67888-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="67888-110">[in] Sembol deposu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="67888-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="67888-111">[in] Alternatif olarak kullanılan dosya akışı `filename` parametresi.</span><span class="sxs-lookup"><span data-stu-id="67888-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67888-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="67888-112">Return Value</span></span>  
 <span data-ttu-id="67888-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="67888-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67888-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67888-114">Requirements</span></span>  
 <span data-ttu-id="67888-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="67888-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67888-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67888-116">See Also</span></span>  
 [<span data-ttu-id="67888-117">Isymunmanagedreader arabirimi</span><span class="sxs-lookup"><span data-stu-id="67888-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
