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
ms.openlocfilehash: f40b99c0a81bf0f2b622c7d23157dbb5736df1ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403298"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="847d0-102">GetWin32ResBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="847d0-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="847d0-103">Win32 kaynak blob alır.</span><span class="sxs-lookup"><span data-stu-id="847d0-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="847d0-104">Derleme seçenekleri ayarladıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="847d0-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="847d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="847d0-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="847d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="847d0-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="847d0-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="847d0-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="847d0-108">Win32 sürümü kaynak oluşturulurken kullanılacak dosya adını almak için kullanılan dosya simgesi</span><span class="sxs-lookup"><span data-stu-id="847d0-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="847d0-109">Dosya bir DLL için bir EXE false ise, TRUE.</span><span class="sxs-lookup"><span data-stu-id="847d0-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="847d0-110">Kaynak blob'a eklemek için isteğe bağlı simge.</span><span class="sxs-lookup"><span data-stu-id="847d0-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="847d0-111">Kaynak blob alır.</span><span class="sxs-lookup"><span data-stu-id="847d0-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="847d0-112">Kabarcık boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="847d0-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="847d0-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="847d0-113">Return Value</span></span>  
 <span data-ttu-id="847d0-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="847d0-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="847d0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="847d0-115">Requirements</span></span>  
 <span data-ttu-id="847d0-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="847d0-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="847d0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="847d0-117">See Also</span></span>  
 [<span data-ttu-id="847d0-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="847d0-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="847d0-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="847d0-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="847d0-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="847d0-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
