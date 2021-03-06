---
title: 'Son değişiklik: tek dosya yayımlama biçimi için derlemeden ilgili API davranışı değişiklikleri'
description: Bir derlemenin dosya konumuyla ilgili birden çok API 'nin, tek dosya yayımlama biçiminde çağrıldığında davranış değişikliklerinin olduğu çekirdek .NET kitaplıklarında .NET 5 ' in son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 3810a71fac481a42ccf2c8e64149d171f31c6821
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257693"
---
# <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a>Tek dosya yayımlama biçimi için derlemeden ilgili API davranışı değişiklikleri

Bir derlemenin dosya konumuyla ilgili birden çok API, tek dosya yayımlama biçiminde çağrıldığında davranış değişikliklerine sahiptir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 ve sonraki sürümler için tek dosya yayımlama sürümünde, paketlenmiş derlemeler diske ayıklanmak yerine bellekten yüklenir. Tek dosya yayımlanan uygulamalar için bu, konumla ilgili bazı API 'Lerin .NET 5 ve sonraki sürümlerini önceki .NET sürümlerinden farklı şekilde döndürdüğü anlamına gelir. Değişiklikler aşağıdaki gibidir:

| API | Önceki sürümler | .NET 5 ve üzeri |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | Ayıklanan DLL dosyası yolunu döndürür | Paketlenmiş derlemeler için boş dize döndürür |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | Ayıklanan DLL dosyası yolunu döndürür | Paketlenmiş derlemeler için özel durum oluşturur |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | `null`Paketlenmiş derlemeler için döndürür | Paketlenmiş derlemeler için özel durum oluşturur |
| `Environment.GetCommandLineArgs()[0]` | Değer, giriş noktası DLL 'inin adıdır | Değer, ana bilgisayarın yürütülebilir dosyasının adıdır |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | Değer, geçici ayıklama dizinidir | Değer, ana bilgisayarın yürütülebilir dosyasının bulunduğu dizin |

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Tek bir dosya olarak yayımlarken derlemelerin dosya konumundaki bağımlılıklardan kaçının.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
