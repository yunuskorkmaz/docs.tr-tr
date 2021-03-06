---
title: 'Son değişiklik: Cryptography. OID yalnızca işlev olarak init'
description: .NET 5 ' teki son değişiklik hakkında bilgi edinin. OID sınıfında özellik ayarlayıcıları artık bir değeri değiştirmeye çalışırsanız bir özel durum oluşturur.
ms.date: 08/16/2020
ms.openlocfilehash: aa1e72adcda61f2292574729e36cdc578bf907d2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256874"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a>System. Security. Cryptography. OID yalnızca işlev olarak init

<xref:System.Security.Cryptography.Oid?displayProperty=fullName>ASN. 1 nesne tanımlayıcı değerlerini ve "kolay" adlarını temsil etmek için kullanılan sınıfı, daha önce tamamen kesilebilir. Bu sıklık genellikle daha fazla bakmıştı veya sürpriz olarak geldi. Özellik ayarlayıcıları artık, <xref:System.PlatformNotSupportedException> zaten atandıktan sonra değeri değiştirmeye çalıştığınızda bir oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki sürümlerde özellik ayarlayıcıları, <xref:System.Security.Cryptography.Oid> ve özelliklerinin değerini değiştirmek için kullanılabilir <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> .

.NET 5 ve sonraki sürümlerde özellik ayarlayıcıları yalnızca değeri başlatmak için kullanılabilir. Özelliğin bir oluşturucudan veya özellik ayarlayıcısına yapılan bir çağrıdan bir değere sahip olması durumunda, Özellik ayarlayıcısı her zaman bir oluşturur <xref:System.PlatformNotSupportedException> .

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, <xref:System.Security.Cryptography.Oid> nesne ayırma profillerini azaltmak için genel API 'lerde döndürülen değerlerin bir parçası olarak nesnelerin yeniden kullanılmasını sağlar. Değerler giriş olarak kullanıldığında geçici "savunma" kopyalarının oluşturulması gereksinimini önler <xref:System.Security.Cryptography.Oid> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

<xref:System.Security.Cryptography.Oid>Nesne başlatma için dışında özellik ayarlayıcıları kullanmaktan kaçının. Yeni bir değeri göstermek için, varolan bir nesne üzerindeki değeri değiştirmek yerine yeni bir örnek kullanın.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

### Category

Cryptography

-->
