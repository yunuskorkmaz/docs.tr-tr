---
title: .NET 5 + ' da kullanımdan kalkmış Özellikler
description: .NET 5,0 ve sonraki sürümlerde eski olarak işaretlenen ve SYSLIB Derleyici uyarıları üreten API 'Ler hakkında bilgi edinin.
ms.date: 10/20/2020
ms.openlocfilehash: 13f5fb10cfe693ed621b3f45fc22e024875890c8
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333354"
---
# <a name="obsolete-features-in-net-5"></a>.NET 5 ' teki kullanımdan kalkmış Özellikler

.NET 5,0 ' den itibaren, yeni olarak eski olarak işaretlenen bazı API 'Ler üzerinde iki yeni özelliği kullanır <xref:System.ObsoleteAttribute> .

- <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType>Özelliği derleyiciye özel bir tanılama kimliği kullanarak derleme uyarıları oluşturmasını söyler. Özel KIMLIK, kullanımdan çıkarma uyarısının özellikle ve birbirinden ayrı bir şekilde gizlenmasını sağlar. .NET 5 + kullanımdan kullanım durumunda, özel tanılama KIMLIĞI için biçim `SYSLIBxxxx` .

- <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType>Özelliği, derleyicinin kullanımdan çıkarılması hakkında daha fazla bilgi edinmek için BIR URL bağlantısı içermesini söyler.

Kullanılmayan bir API kullanımı nedeniyle derleme uyarıları veya hatalarıyla karşılaşırsanız, [başvuru](#reference) bölümünde LISTELENEN tanılama kimliği için verilen belirli bir kılavuzu izleyin. Eski türler veya Üyeler için [standart tanılama kimliği (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) kullanılarak bu kullanımdan *kaldırılmaları uyarıları veya hataları gizlenemedi* ; `SYSLIBxxxx`bunun yerine özel tanılama kimliği değerlerini kullanın. Daha fazla bilgi için bkz. [uyarıları gösterme](#suppress-warnings).

## <a name="reference"></a>Başvuru

Aşağıdaki tabloda, `SYSLIBxxxx` .NET 5 + ' de kullanımdan çıkarılan bir dizin verilmiştir.

| Tanılama KIMLIĞI | Description |
| - | - |
| [SYSLIB0001](syslib0001.md) | UTF-7 kodlaması güvenli değil ve kullanılmamalıdır. Bunun yerine UTF-8 kullanmayı düşünün. |
| [SYSLIB0002](syslib0002.md) | <xref:System.Security.Permissions.PrincipalPermissionAttribute> çalışma zamanı tarafından kabul edilmez ve kullanılmamalıdır. |
| [SYSLIB0003](syslib0003.md) | Kod erişim güvenliği (CAS) çalışma zamanı tarafından desteklenmez veya kabul edilmez. |
| [SYSLIB0004](syslib0004.md) | Kısıtlanmış yürütme bölgesi (CER) özelliği desteklenmiyor. |
| [SYSLIB0005](syslib0005.md) | Genel bütünleştirilmiş kod önbelleği (GAC) desteklenmiyor. |
| [SYSLIB0006](syslib0006.md) | <xref:System.Threading.Thread.Abort?displayProperty=nameWithType> desteklenmez ve atar <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0007](syslib0007.md) | Bu şifreleme algoritmasının varsayılan uygulanması desteklenmiyor. |
| [SYSLIB0008](syslib0008.md) | <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator>API desteklenmez ve atar <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0009](syslib0009.md) | <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>Ve <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> yöntemleri desteklenmez ve throw <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0010](syslib0010.md) | Bazı uzaktan iletişim API 'Leri desteklenmez ve throw <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0011](syslib0011.md) | <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serileştirme artık kullanılmıyor ve kullanılmamalıdır. |
| [SYSLIB0012](syslib0012.md) | <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> ve <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> yalnızca .NET Framework uyumluluk için dahil edilmiştir. Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın. |

## <a name="suppress-warnings"></a>Uyarıları gizleme

Kullanılmayan API 'Leri kullanmanız gerekiyorsa ve `SYSLIBxxxx` tanı hata olarak gösterilmezse, koddaki veya proje dosyanızdaki uyarıyı gizleyebilirsiniz.

Kod:

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

Proje dosyası:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> Bu şekilde bir uyarının gizlenmesi yalnızca belirli bir kullanımdan kaldırma uyarısını devre dışı bırakır. Diğer kullanımdan çıkarma uyarıları dahil diğer uyarıları devre dışı bırakır.
