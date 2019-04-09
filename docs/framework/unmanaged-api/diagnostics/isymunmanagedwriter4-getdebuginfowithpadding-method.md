---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 191aa16c285b3a28beed65004d65525c9214ec93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081579"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="d913e-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu</span><span class="sxs-lookup"><span data-stu-id="d913e-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="d913e-103">Aynı şekilde işler [Getdebugınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) yol dizesi sabit bir boyuta dize verileri yapmak için bir sonlandırıcı null karakteri aşağıdaki sıfırlarla dışında `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="d913e-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="d913e-104">Doldurma yolu dize uzunluğu kendisi ise yalnızca verilen küçüktür `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="d913e-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="d913e-105">Bu araçlar, fark PE dosyaları yazmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d913e-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d913e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d913e-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d913e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d913e-107">Parameters</span></span>  
  
|<span data-ttu-id="d913e-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="d913e-108">Parameter</span></span>|<span data-ttu-id="d913e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d913e-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="d913e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d913e-110">Return Value</span></span>  
 <span data-ttu-id="d913e-111">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d913e-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d913e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d913e-112">Requirements</span></span>  
 <span data-ttu-id="d913e-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d913e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d913e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d913e-114">See also</span></span>

- [<span data-ttu-id="d913e-115">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d913e-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
