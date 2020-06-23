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
# <a name="unsafenclnativemethods-class"></a>UnsafeNclNativeMethods sınıfı

Güvenli olmayan yerel ağ yöntemlerini içe alan sınıflar içerir. Bu sınıf devralınamaz.

```csharp
internal static class UnsafeNclNativeMethods
```

> [!WARNING]
> Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="nativepki-class"></a>NativePKI sınıfı

crypt32.dll içeri aktarılan yöntemleri içerir. Bu yöntemler, Köprü Metni Aktarım Protokolü güvenli (HTTPS) kullanılırken sertifikaları işler. Bu sınıf devralınamaz.

```csharp
internal static class NativePKI
```

## <a name="nativepkifindclientcertificates-method"></a>Nativepkı. FindClientCertificates yöntemi

Sunucuya göndermek için kullanılabilir istemci sertifikalarını bulur.

```csharp
internal static X509CertificateCollection FindClientCertificates
```

### <a name="return-value"></a>Döndürülen değer

<xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection?displayProperty=nameWithType>

Kullanılabilir istemci sertifikalarının bir koleksiyonu.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)
