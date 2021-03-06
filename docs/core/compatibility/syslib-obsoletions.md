---
title: .NET 5 + ' da kullanımdan kalkmış Özellikler
description: .NET 5 ' te kullanımdan kaldırılmış olarak işaretlenen API 'Ler ve SYSLIB Derleyici uyarıları üreten sürümler hakkında bilgi edinin.
ms.date: 10/20/2020
ms.openlocfilehash: d6563f21624456d74801242268ecf72652fc4f88
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256289"
---
# <a name="obsolete-features-in-net-5"></a>.NET 5 ' teki kullanımdan kalkmış Özellikler

.NET 5 ' den itibaren, yeni olarak eski olarak işaretlenen bazı API 'Ler üzerinde iki yeni özelliği kullanır <xref:System.ObsoleteAttribute> .

- <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType>Özelliği derleyiciye özel bir tanılama kimliği kullanarak derleme uyarıları oluşturmasını söyler. Özel KIMLIK, kullanımdan çıkarma uyarısının özellikle ve birbirinden ayrı bir şekilde gizlenmasını sağlar. .NET 5 + kullanımdan kullanım durumunda, özel tanılama KIMLIĞI için biçim `SYSLIBxxxx` .

- <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType>Özelliği, derleyicinin kullanımdan çıkarılması hakkında daha fazla bilgi edinmek için BIR URL bağlantısı içermesini söyler.

Kullanılmayan bir API kullanımı nedeniyle derleme uyarıları veya hatalarıyla karşılaşırsanız, [başvuru](#reference) bölümünde LISTELENEN tanılama kimliği için verilen belirli bir kılavuzu izleyin. Eski türler veya Üyeler için [standart tanılama kimliği (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) kullanılarak bu kullanımdan *kaldırılmaları uyarıları veya hataları gizlenemedi* ; `SYSLIBxxxx`bunun yerine özel tanılama kimliği değerlerini kullanın. Daha fazla bilgi için bkz. [uyarıları gösterme](#suppress-warnings).

## <a name="reference"></a>Başvuru

Aşağıdaki tabloda, `SYSLIBxxxx` .NET 5 + ' de kullanımdan çıkarılan bir dizin verilmiştir.

| Tanılama KIMLIĞI | Açıklama |
| - | - |
| [SYSLIB0001](syslib-warnings/syslib0001.md) | UTF-7 kodlaması güvenli değil ve kullanılmamalıdır. Bunun yerine UTF-8 kullanmayı düşünün. |
| [SYSLIB0002](syslib-warnings/syslib0002.md) | <xref:System.Security.Permissions.PrincipalPermissionAttribute> çalışma zamanı tarafından kabul edilmez ve kullanılmamalıdır. |
| [SYSLIB0003](syslib-warnings/syslib0003.md) | Kod erişim güvenliği (CAS) çalışma zamanı tarafından desteklenmez veya kabul edilmez. |
| [SYSLIB0004](syslib-warnings/syslib0004.md) | Kısıtlanmış yürütme bölgesi (CER) özelliği desteklenmiyor. |
| [SYSLIB0005](syslib-warnings/syslib0005.md) | Genel bütünleştirilmiş kod önbelleği (GAC) desteklenmiyor. |
| [SYSLIB0006](syslib-warnings/syslib0006.md) | <xref:System.Threading.Thread.Abort?displayProperty=nameWithType> desteklenmez ve atar <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0007](syslib-warnings/syslib0007.md) | Bu şifreleme algoritmasının varsayılan uygulanması desteklenmiyor. |
| [SYSLIB0008](syslib-warnings/syslib0008.md) | <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator>API desteklenmez ve atar <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0009](syslib-warnings/syslib0009.md) | <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>Ve <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> yöntemleri desteklenmez ve throw <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0010](syslib-warnings/syslib0010.md) | Bazı uzaktan iletişim API 'Leri desteklenmez ve throw <xref:System.PlatformNotSupportedException> . |
| [SYSLIB0011](syslib-warnings/syslib0011.md) | <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serileştirme artık kullanılmıyor ve kullanılmamalıdır. |
| [SYSLIB0012](syslib-warnings/syslib0012.md) | <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> ve <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> yalnızca .NET Framework uyumluluk için dahil edilmiştir. Bunun yerine <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> kullanın. |

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
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> Uyarıları bu şekilde gizleme yalnızca belirttiğiniz kullanımdan kaldırma uyarılarını devre dışı bırakır. Farklı tanılama kimliklerine sahip kullanımdan çıkarma uyarıları dahil diğer uyarıları devre dışı bırakır.
