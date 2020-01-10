---
title: HttpWebRequest. _CoreResponse alanı
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740453"
---
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="9eb18-102">HttpWebRequest.\_CoreResponse alanı</span><span class="sxs-lookup"><span data-stu-id="9eb18-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="9eb18-103">`HttpWebRequest._CoreResponse`, HTTP yanıtı ayrıştırma sonucunu içeren bir nesnedir (bir [CoreResponseData](coreresponsedata.md) veya <xref:System.Exception>).</span><span class="sxs-lookup"><span data-stu-id="9eb18-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="9eb18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9eb18-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="9eb18-105">Bu API 'nin doğrudan kodunuzda kullanılması amaçlıyordu.</span><span class="sxs-lookup"><span data-stu-id="9eb18-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="9eb18-106">Bunun yerine, ağ kodunu bağlamak için bir <xref:System.Diagnostics.DiagnosticSource> kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9eb18-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="9eb18-107">Bkz. [Diagnosticsource Kullanıcı Kılavuzu](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="9eb18-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="9eb18-108">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9eb18-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9eb18-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9eb18-109">Requirements</span></span>

<span data-ttu-id="9eb18-110">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="9eb18-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="9eb18-111">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="9eb18-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="9eb18-112">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9eb18-112">**.NET Framework versions:** Available since 2.0.</span></span>
