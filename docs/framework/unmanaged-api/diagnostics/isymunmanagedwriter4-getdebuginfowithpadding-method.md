---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 274bf79175bda9e880b1ef3cf8f125a017ad0734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121667"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="fd54f-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Metodu</span><span class="sxs-lookup"><span data-stu-id="fd54f-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="fd54f-103">Dize verilerini sabit bir `MAX_PATH`boyutuna getirmek için, yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="fd54f-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="fd54f-104">Padding yalnızca yol dize uzunluğunun `MAX_PATH`' den küçük olması durumunda verilir.</span><span class="sxs-lookup"><span data-stu-id="fd54f-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="fd54f-105">Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fd54f-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd54f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd54f-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd54f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd54f-107">Parameters</span></span>  
  
|<span data-ttu-id="fd54f-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="fd54f-108">Parameter</span></span>|<span data-ttu-id="fd54f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd54f-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="fd54f-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd54f-110">Return Value</span></span>  
 <span data-ttu-id="fd54f-111">`HRESULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd54f-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd54f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd54f-112">Requirements</span></span>  
 <span data-ttu-id="fd54f-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fd54f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd54f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd54f-114">See also</span></span>

- [<span data-ttu-id="fd54f-115">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd54f-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
