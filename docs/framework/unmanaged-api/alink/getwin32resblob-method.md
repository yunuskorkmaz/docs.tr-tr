---
title: GetWin32ResBlob Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: GetWin32ResBlob
helpviewer_keywords: GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c4456757c56440463010d4adc3d3eed90dbc07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="8acef-102">GetWin32ResBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="8acef-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="8acef-103">Win32 kaynak blob alır.</span><span class="sxs-lookup"><span data-stu-id="8acef-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="8acef-104">Derleme seçenekleri ayarladıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="8acef-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8acef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8acef-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8acef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8acef-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8acef-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="8acef-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8acef-108">Win32 sürümü kaynak oluşturulurken kullanılacak dosya adını almak için kullanılan dosya simgesi</span><span class="sxs-lookup"><span data-stu-id="8acef-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="8acef-109">Dosya bir DLL için bir EXE false ise, TRUE.</span><span class="sxs-lookup"><span data-stu-id="8acef-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="8acef-110">Kaynak blob'a eklemek için isteğe bağlı simge.</span><span class="sxs-lookup"><span data-stu-id="8acef-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="8acef-111">Kaynak blob alır.</span><span class="sxs-lookup"><span data-stu-id="8acef-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="8acef-112">Kabarcık boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="8acef-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8acef-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8acef-113">Return Value</span></span>  
 <span data-ttu-id="8acef-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8acef-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8acef-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8acef-115">Requirements</span></span>  
 <span data-ttu-id="8acef-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="8acef-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8acef-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8acef-117">See Also</span></span>  
 [<span data-ttu-id="8acef-118">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="8acef-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8acef-119">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8acef-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8acef-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="8acef-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
