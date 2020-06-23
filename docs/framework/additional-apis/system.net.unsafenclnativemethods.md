---
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
ms.openlocfilehash: 46756a0d1d69b4768dbb8dcdd7ab098d3f1849bf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990357"
---
# <a name="unsafenclnativemethods-class"></a><span data-ttu-id="a350b-102">UnsafeNclNativeMethods sınıfı</span><span class="sxs-lookup"><span data-stu-id="a350b-102">UnsafeNclNativeMethods class</span></span>

<span data-ttu-id="a350b-103">Güvenli olmayan yerel ağ yöntemlerini içe alan sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="a350b-103">Contains classes that import unsafe native networking methods.</span></span> <span data-ttu-id="a350b-104">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="a350b-104">This class cannot be inherited.</span></span>

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> <span data-ttu-id="a350b-105">Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a350b-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a350b-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a350b-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="nativepki-class"></a><span data-ttu-id="a350b-107">NativePKI sınıfı</span><span class="sxs-lookup"><span data-stu-id="a350b-107">NativePKI class</span></span>

<span data-ttu-id="a350b-108">crypt32.dll içeri aktarılan yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a350b-108">Contains methods imported from crypt32.dll.</span></span> <span data-ttu-id="a350b-109">Bu yöntemler, Köprü Metni Aktarım Protokolü güvenli (HTTPS) kullanılırken sertifikaları işler.</span><span class="sxs-lookup"><span data-stu-id="a350b-109">These methods handle certificates when using Hypertext Transfer Protocol Secure (HTTPS).</span></span> <span data-ttu-id="a350b-110">Bu sınıf devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="a350b-110">This class cannot be inherited.</span></span>

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a><span data-ttu-id="a350b-111">Nativepkı. FindClientCertificates yöntemi</span><span class="sxs-lookup"><span data-stu-id="a350b-111">NativePKI.FindClientCertificates method</span></span>

<span data-ttu-id="a350b-112">Sunucuya göndermek için kullanılabilir istemci sertifikalarını bulur.</span><span class="sxs-lookup"><span data-stu-id="a350b-112">Discovers available client certificates to send to the server.</span></span>

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a><span data-ttu-id="a350b-113">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="a350b-113">Return value</span></span>

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

<span data-ttu-id="a350b-114">Kullanılabilir istemci sertifikalarının bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a350b-114">A collection of available client certificates.</span></span>

## <a name="requirements"></a><span data-ttu-id="a350b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a350b-115">Requirements</span></span>

<span data-ttu-id="a350b-116">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a350b-116">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a350b-117">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="a350b-117">**Assembly:** System (in System.dll)</span></span>
