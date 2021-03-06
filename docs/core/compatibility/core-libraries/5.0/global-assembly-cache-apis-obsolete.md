---
title: "Son değişiklik: genel bütünleştirilmiş kod önbelleği API 'Leri artık kullanılmıyor"
description: GAC ile ilgilenen API 'Lerin başarısız olduğu veya hiçbir işlem gerçekleştirdiği çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 39c7b092b06754a28723693c0147b7ec3a0b705e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257485"
---
# <a name="global-assembly-cache-apis-are-obsolete"></a>Genel bütünleştirilmiş kod önbelleği API 'Leri artık kullanılmıyor

.NET Core ve .NET 5 ve sonraki sürümleri, .NET Framework mevcut olan genel derleme önbelleği (GAC) kavramını ortadan kaldırır. Bu nedenle, GAC ile ilgilenen tüm .NET Core ve .NET 5 + API 'Leri başarısız olur ya da hiçbir işlem gerçekleştirmez.

Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için GAC ile ilgili bazı API 'Ler eski olarak işaretlenir ve `SYSLIB0005` derleme zamanında bir uyarı oluşturur. Bu API 'Ler, .NET 'in gelecek bir sürümünde kaldırılabilir.

## <a name="change-description"></a>Açıklamayı Değiştir

Aşağıdaki API 'Ler kullanılmıyor olarak işaretlendi.

| API | İçinde kullanılmıyor olarak işaretlendi... |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | 5,0 RC1 |

.NET Framework 2. x-4. x içinde, <xref:System.Reflection.Assembly.GlobalAssemblyCache> `true` SORGULANAN derleme GAC 'den yüklenmişse ve `false` disk üzerindeki farklı bir konumdan yüklenmişse, özelliği döndürür. .NET Core 2. x-3. x içinde <xref:System.Reflection.Assembly.GlobalAssemblyCache> her zaman döndürülür ve `false` GAC 'Nin .NET Core 'da mevcut olmadığını yansıtır.

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

.NET 5 ve sonraki sürümlerde <xref:System.Reflection.Assembly.GlobalAssemblyCache> özelliği her zaman döndürülür `false` . Ancak, özellik alıcısı, özelliğe erişmeyi durdurmasına izin veren çağıranlar belirtmek için artık kullanılmıyor olarak işaretlenir. Kitaplıklar ve uygulamalar <xref:System.Reflection.Assembly.GlobalAssemblyCache> , her zaman `false` .NET Core ve .NET 5 ve sonraki sürümlerde döndürdüğü için, çalışma zamanı davranışı hakkında belirleyici hale getirmek üzere API 'yi kullanmamalıdır.

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

Bu yalnızca derleme zamanı değişir. .NET Core 'un önceki sürümlerinden çalışma zamanı değişikliği yoktur.

## <a name="reason-for-change"></a>Değişiklik nedeni

Genel bütünleştirilmiş kod önbelleği (GAC), .NET Core ve .NET 5 ve sonraki sürümlerde bir kavram olarak mevcut değildir.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5.0

## <a name="recommended-action"></a>Önerilen eylem

- Uygulamanız özelliği sorgularsa <xref:System.Reflection.Assembly.GlobalAssemblyCache> , çağrıyı kaldırmayı göz önünde bulundurun. "GAC 'de olmayan bir derleme" ile "bir <xref:System.Reflection.Assembly.GlobalAssemblyCache> " bütünleştirilmiş kod ") arasında seçim yapmak için değeri kullanırsanız, çalışma zamanında Flow 'un bir .NET Core veya .NET 5.0 + uygulaması için hala mantıklı olup olmadığını yeniden düşünün.

- Kullanılmayan API 'Leri kullanmaya devam etmeniz gerekiyorsa, `SYSLIB0005` koddaki uyarıyı gizleyebilirsiniz.

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  Proje dosyanızda, projedeki tüm kaynak dosyaları için uyarıyı devre dışı bırakan uyarıyı da gizleyebilirsiniz.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  Gizleme `SYSLIB0005` yalnızca kullanımdan kaldırma uyarısını devre dışı bırakır <xref:System.Reflection.Assembly.GlobalAssemblyCache> . Başka herhangi bir uyarıyı devre dışı bırakır.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
