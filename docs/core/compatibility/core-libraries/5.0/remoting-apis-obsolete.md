---
title: "Son değişiklik: uzaktan Iletişim API 'Leri artık kullanılmıyor"
description: Remoting ile ilgili bazı API 'Lerin eski olarak işaretlendikleri ve özel bir tanılama KIMLIĞIYLE uyarı oluşturulduğu çekirdek .NET kitaplıklarında .NET 5,0 'in son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 5687b1471028b077674cfd31cb77ce95dc51bef5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761498"
---
# <a name="remoting-apis-are-obsolete"></a>Uzaktan iletişim API 'Leri artık kullanılmıyor

Remoting ile ilgili bazı API 'Ler kullanılmıyor olarak işaretlenir ve `SYSLIB0010` derleme zamanında bir uyarı oluşturur. Bu API 'Ler, .NET 'in gelecek bir sürümünde kaldırılabilir.

## <a name="change-description"></a>Açıklamayı Değiştir

Aşağıdaki uzaktan iletişim API 'Leri kullanılmıyor olarak işaretlenir.

| API | İçinde kullanılmıyor olarak işaretlendi... |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | 5,0 RC1 |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | 5,0 RC1 |

.NET Framework 2. x-4. x içinde, <xref:System.MarshalByRefObject.GetLifetimeService> ve <xref:System.MarshalByRefObject.InitializeLifetimeService> yöntemleri .NET uzaktan iletişim ile ilgili örneklerin ömrünü denetler. .NET Core 2. x-3. x içinde, bu yöntemler her zaman çalışma zamanında oluşturur <xref:System.PlatformNotSupportedException> .

.NET 5,0 ve sonraki sürümlerinde, <xref:System.MarshalByRefObject.GetLifetimeService> ve <xref:System.MarshalByRefObject.InitializeLifetimeService> yöntemleri uyarı olarak kullanımdan kalkmıştır, ancak çalışma zamanında bir oluşturma işlemine devam eder <xref:System.PlatformNotSupportedException> .

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

Bu yalnızca derleme zamanı değişir. .NET Core 'un önceki sürümlerinden çalışma zamanı değişikliği yoktur.

## <a name="reason-for-change"></a>Değişiklik nedeni

[.NET uzaktan iletişim](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) , eski bir teknolojidir. Başka bir işlemdeki (potansiyel olarak farklı bir makinede bile) bir nesnenin örneğini oluşturma ve bu nesneyle normal, işlem içi bir .NET nesne örneği gibi etkileşim kurma olanağı sağlar. .NET uzaktan iletişim altyapısı yalnızca .NET Framework 2. x-4. x içinde bulunur. .NET Core ve .NET 5,0 ve üzeri sürümlerde .NET uzaktan iletişim desteği yoktur ve uzaktan iletişim API 'Leri yok ya da bu çalışma zamanları üzerinde her zaman özel durum oluşturmaz.

Geliştiricilerin bu API 'lerden uzaklaşmasına yardımcı olmak için, Remoting ile ilgili seçili API 'Leri kullanımdan çıkaracağız. Bu API 'Ler tamamen .NET 'in gelecek bir sürümünde kaldırılabilir.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0

## <a name="recommended-action"></a>Önerilen eylem

- Diğer uygulamalardaki veya makinelerde bulunan nesnelerle iletişim kurmak için WCF veya HTTP tabanlı REST hizmetlerini kullanmayı göz önünde bulundurun. Daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../../porting/net-framework-tech-unavailable.md).

- Kullanılmayan API 'Leri kullanmaya devam etmeniz gerekiyorsa, `SYSLIB0010` koddaki uyarıyı gizleyebilirsiniz.

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  Proje dosyanızda, projedeki tüm kaynak dosyaları için uyarıyı devre dışı bırakan uyarıyı da gizleyebilirsiniz.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  Gizleme `SYSLIB0010` yalnızca uzak API kullanımdan kaldırma uyarılarını devre dışı bırakır. Başka herhangi bir uyarıyı devre dışı bırakır. Ayrıca, her zaman atma için sürekli kodlanmış çalışma zamanı davranışını değiştirmez <xref:System.PlatformNotSupportedException> .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
