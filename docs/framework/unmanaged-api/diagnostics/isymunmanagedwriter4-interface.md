---
title: ISymUnmanagedWriter4 Arabirimi
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: a656777461c50b5a1593917278eb54abda982dc2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134561"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="8e759-102">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e759-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="8e759-103">ISymUnmanagedWriter4 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8e759-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e759-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e759-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="8e759-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8e759-105">Methods</span></span>  
 <span data-ttu-id="8e759-106">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8e759-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="8e759-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8e759-107">Method</span></span>|<span data-ttu-id="8e759-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e759-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e759-109">GetDebugInfoWithPadding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e759-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="8e759-110">Dize verilerini sabit bir `MAX_PATH`boyutuna getirmek için, yol dizesinin Sonlandırıcı null karakteri izleyen sıfırlarla doldurulmasının dışında, [GetDebugInfo yöntemiyle](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) aynı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="8e759-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="8e759-111">Padding yalnızca yol dize uzunluğunun `MAX_PATH`' den küçük olması durumunda verilir.</span><span class="sxs-lookup"><span data-stu-id="8e759-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="8e759-112">Bu, farklı PE dosyalarına sahip araçların yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8e759-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e759-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e759-113">Requirements</span></span>  
 <span data-ttu-id="8e759-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8e759-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e759-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e759-115">See also</span></span>

- [<span data-ttu-id="8e759-116">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8e759-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="8e759-117">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e759-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
