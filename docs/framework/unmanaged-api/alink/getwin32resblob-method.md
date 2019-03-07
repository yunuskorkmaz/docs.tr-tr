---
title: GetWin32ResBlob Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 295b150f6881a47b3816a93ac7a20382bc5c20c0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500583"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="a29ab-102">GetWin32ResBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="a29ab-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="a29ab-103">Win32 kaynak blob alır.</span><span class="sxs-lookup"><span data-stu-id="a29ab-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="a29ab-104">Derleme Seçenekleri'ni ayarladıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="a29ab-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29ab-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a29ab-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a29ab-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a29ab-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a29ab-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="a29ab-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a29ab-108">Win32 sürüm kaynağı oluşturulurken kullanılacak dosya adını almak için kullanılan dosya simgesi</span><span class="sxs-lookup"><span data-stu-id="a29ab-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="a29ab-109">Dosya bir DLL için bir EXE false ise, TRUE.</span><span class="sxs-lookup"><span data-stu-id="a29ab-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="a29ab-110">Kaynak blob eklenecek isteğe bağlı simge.</span><span class="sxs-lookup"><span data-stu-id="a29ab-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="a29ab-111">Kaynak blob alır.</span><span class="sxs-lookup"><span data-stu-id="a29ab-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="a29ab-112">Kabarcık boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="a29ab-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a29ab-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a29ab-113">Return Value</span></span>  
 <span data-ttu-id="a29ab-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="a29ab-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a29ab-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a29ab-115">Requirements</span></span>  
 <span data-ttu-id="a29ab-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="a29ab-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29ab-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a29ab-117">See also</span></span>
- [<span data-ttu-id="a29ab-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a29ab-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a29ab-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a29ab-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a29ab-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="a29ab-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
