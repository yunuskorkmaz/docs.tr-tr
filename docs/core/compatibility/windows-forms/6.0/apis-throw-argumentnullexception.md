---
title: "Son değişiklik: bazı API 'Ler bağımsız değişkenler NullException oluşturur"
description: .NET 6 ' daki Son değişiklik hakkında bilgi edinmek için bazı API 'Lerin bağımsız değişkenleri doğruladığını ve şimdi bir ArgumentNullException oluşturacağı
ms.date: 01/29/2021
ms.openlocfilehash: ca7f32739237715657350f52d2523b0ce378364d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255743"
---
# <a name="some-apis-throw-argumentnullexception"></a>Bazı API 'Ler bağımsız değişkenler NullException oluşturur

Bazı API 'Ler artık giriş parametrelerini doğrular ve <xref:System.ArgumentNullException> <xref:System.NullReferenceException> giriş bağımsız değişkenleriyle çağrılırsa daha önce oluşturduğu yerleri oluşturur `null` .

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, etkilenen API 'Ler, bir <xref:System.NullReferenceException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .

.NET 6 ' dan itibaren, etkilenen API 'Ler bir <xref:System.ArgumentNullException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .

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
