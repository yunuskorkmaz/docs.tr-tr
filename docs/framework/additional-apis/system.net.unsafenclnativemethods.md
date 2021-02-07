---
description: 'Daha fazla bilgi edinin: UnsafeNclNativeMethods sınıfı'
title: UnsafeNclNativeMethods sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.UnsafeNclNativeMethods
- System.Net.UnsafeNclNativeMethods.NativePKI
- System.Net.UnsafeNclNativeMethods.NativePKI.FindClientCertificates
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fa1084efddae0ba5cbfc9a949dcd94d2c64f3272
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699499"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="644fa-103">UnsafeNclNativeMethods sınıfı</span><span class="sxs-lookup"><span data-stu-id="644fa-103">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="644fa-104">Güvenli olmayan yerel ağ yöntemlerini içe alan sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="644fa-104">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="644fa-105">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="644fa-105">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="644fa-106">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="644fa-106">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="644fa-107">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="644fa-107">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="644fa-108">NativePKI sınıfı</span><span class="sxs-lookup"><span data-stu-id="644fa-108">NativePKI class</span></span>

<span data-ttu-id="644fa-109">crypt32.dll içeri aktarılan yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="644fa-109">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="644fa-110">Bu yöntemler, Köprü Metni Aktarım Protokolü güvenli (HTTPS) kullanılırken sertifikaları işler.</span><span class="sxs-lookup"><span data-stu-id="644fa-110">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="644fa-111">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="644fa-111">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="644fa-112">Nativepkı. FindClientCertificates yöntemi</span><span class="sxs-lookup"><span data-stu-id="644fa-112">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="644fa-113">Sunucuya göndermek için kullanılabilir istemci sertifikalarını bulur.</span><span class="sxs-lookup"><span data-stu-id="644fa-113">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="644fa-114">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="644fa-114">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="644fa-115">Kullanılabilir istemci sertifikalarının bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="644fa-115">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="644fa-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="644fa-116">Requirements</span></span>

<span data-ttu-id="644fa-117">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="644fa-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="644fa-118">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="644fa-118">**Assembly:** System (in System.dll)</span></span>
