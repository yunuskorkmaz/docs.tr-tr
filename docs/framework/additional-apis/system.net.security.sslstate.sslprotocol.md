---
title: SslState. SslProtocol özelliği (System .net. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 6983ac071dad29b240308031ecd0a3562a6856e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847201"
---
# <a name="sslstatesslprotocol-property"></a><span data-ttu-id="6160b-102">SslState. SslProtocol özelliği</span><span class="sxs-lookup"><span data-stu-id="6160b-102">SslState.SslProtocol Property</span></span>

<span data-ttu-id="6160b-103">SSL protokolü sürümlerini alır.</span><span class="sxs-lookup"><span data-stu-id="6160b-103">Gets the SSL protocol versions.</span></span>

## <a name="syntax"></a><span data-ttu-id="6160b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6160b-104">Syntax</span></span>

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a><span data-ttu-id="6160b-105">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="6160b-105">Property value</span></span>

<xref:System.Security.Authentication.SslProtocols>  
<span data-ttu-id="6160b-106">SSL protokolü sürümlerini belirten numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="6160b-106">A bitwise combination of the enumeration values that specify the SSL protocol versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="6160b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6160b-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6160b-108">`SslState.SslProtocol` özelliği Dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6160b-108">The `SslState.SslProtocol` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6160b-109">Microsoft, bu özelliğin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6160b-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6160b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6160b-110">Requirements</span></span>

<span data-ttu-id="6160b-111">**Ad alanı:** <xref:System.Net.Security></span><span class="sxs-lookup"><span data-stu-id="6160b-111">**Namespace:** <xref:System.Net.Security></span></span>

<span data-ttu-id="6160b-112">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="6160b-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="6160b-113">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6160b-113">**.NET Framework versions:** Available since 2.0.</span></span>
