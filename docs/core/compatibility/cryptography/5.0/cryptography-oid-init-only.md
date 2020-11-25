---
title: 'Son değişiklik: Cryptography. OID yalnızca işlev olarak init'
description: Cryptography. OID sınıfındaki Özellik ayarlayıcılarının artık bir değeri değiştirmeye çalışırsanız bir özel durum oluşturması için .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 08/16/2020
ms.openlocfilehash: a3b5a393e2a84f7c9a60c2a821ecfda9c6acd2e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761397"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a>System. Security. Cryptography. OID yalnızca işlev olarak init

<xref:System.Security.Cryptography.Oid?displayProperty=fullName>ASN. 1 nesne tanımlayıcı değerlerini ve "kolay" adlarını temsil etmek için kullanılan sınıfı, daha önce tamamen kesilebilir. Bu sıklık genellikle daha fazla bakmıştı veya sürpriz olarak geldi. Özellik ayarlayıcıları artık, <xref:System.PlatformNotSupportedException> zaten atandıktan sonra değeri değiştirmeye çalıştığınızda bir oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki sürümlerde özellik ayarlayıcıları, <xref:System.Security.Cryptography.Oid> ve özelliklerinin değerini değiştirmek için kullanılabilir <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> .

.NET 5,0 ve sonraki sürümlerinde, özellik ayarlayıcıları yalnızca değeri başlatmak için kullanılabilir. Özelliğin bir oluşturucudan veya özellik ayarlayıcısına yapılan bir çağrıdan bir değere sahip olması durumunda, Özellik ayarlayıcısı her zaman bir oluşturur <xref:System.PlatformNotSupportedException> .

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
