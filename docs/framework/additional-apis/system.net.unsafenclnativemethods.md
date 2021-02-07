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
