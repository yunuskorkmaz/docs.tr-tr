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
ms.openlocfilehash: a4c77ade46d2401e2499a94504808efd94f79f93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789798"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="8e115-102">GetWin32ResBlob Metodu</span><span class="sxs-lookup"><span data-stu-id="8e115-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="8e115-103">Win32 kaynak blob alır.</span><span class="sxs-lookup"><span data-stu-id="8e115-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="8e115-104">Derleme Seçenekleri'ni ayarladıktan sonra bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="8e115-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e115-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e115-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8e115-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e115-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8e115-107">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="8e115-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8e115-108">Win32 sürüm kaynağı oluşturulurken kullanılacak dosya adını almak için kullanılan dosya simgesi</span><span class="sxs-lookup"><span data-stu-id="8e115-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="8e115-109">Dosya bir DLL için bir EXE false ise, TRUE.</span><span class="sxs-lookup"><span data-stu-id="8e115-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="8e115-110">Kaynak blob eklenecek isteğe bağlı simge.</span><span class="sxs-lookup"><span data-stu-id="8e115-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="8e115-111">Kaynak blob alır.</span><span class="sxs-lookup"><span data-stu-id="8e115-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="8e115-112">Kabarcık boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="8e115-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e115-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e115-113">Return Value</span></span>  
 <span data-ttu-id="8e115-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e115-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e115-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e115-115">Requirements</span></span>  
 <span data-ttu-id="8e115-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="8e115-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e115-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e115-117">See also</span></span>

- [<span data-ttu-id="8e115-118">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e115-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8e115-119">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e115-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8e115-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="8e115-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
