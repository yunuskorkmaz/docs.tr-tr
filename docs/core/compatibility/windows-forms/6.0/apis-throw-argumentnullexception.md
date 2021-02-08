---
title: "Son değişiklik: bazı API 'Ler bağımsız değişkenler NullException oluşturur"
description: Bazı API 'Lerin bağımsız değişkenleri doğruladığını ve şimdi bir ArgumentNullException oluşturmasını .NET 6,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 01/29/2021
ms.openlocfilehash: f9d7dc8bb57ed8dc5b4ff41bda9b3bde7db7b880
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804168"
---
# <a name="some-apis-throw-argumentnullexception"></a>Bazı API 'Ler bağımsız değişkenler NullException oluşturur

Bazı API 'Ler artık giriş parametrelerini doğrular ve <xref:System.ArgumentNullException> <xref:System.NullReferenceException> giriş bağımsız değişkenleriyle çağrılırsa daha önce oluşturduğu yerleri oluşturur `null` .

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, etkilenen API 'Ler, bir <xref:System.NullReferenceException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .

.NET 6,0 ' den başlayarak, etkilenen API 'Ler bir <xref:System.ArgumentNullException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .

## <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.ArgumentNullException>.NET çalışma zamanı davranışına uygun şekilde oluşturuluyor. Özel duruma neden olan bağımsız değişkeni açıkça iletişim kurarak daha iyi bir hata ayıklama deneyimi sağlar.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 6.0

## <a name="recommended-action"></a>Önerilen eylem

- ' Yi gözden geçirin ve gerekirse, `null` giriş bağımsız değişkenlerinin etkilenen API 'lere geçirilmesini engellemek için kodunuzu güncelleştirin.
- Kodunuz tarafından kullanılıyorsa <xref:System.NullReferenceException> , için ek bir işleyici değiştirin veya ekleyin <xref:System.ArgumentNullException> .

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki tabloda etkilenen özellikler listelenmiştir:

| Özellik | Sürüm değişti |
|-|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | Önizleme 1 |

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
