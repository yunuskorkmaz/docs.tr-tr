---
title: 'Son değişiklik: BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış'
description: BinaryFormatter, Formatter ve IFormatter 'daki serileştirme ve seri durumdan çıkarma yöntemlerinin artık kullanılmayan çekirdek .NET kitaplıklarında .NET 5,0 'in son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 1dca30d33f2aa0a6fe8f05fe728557092f836b2d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189850"
---
# <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a>BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış

`Serialize` ve, `Deserialize` <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , ve üzerindeki yöntemleri <xref:System.Runtime.Serialization.Formatter> <xref:System.Runtime.Serialization.IFormatter> artık uyarı olarak kullanımdan kalkmıştır. Ayrıca, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ASP.NET uygulamaları için serileştirme varsayılan olarak yasaktır.

## <a name="change-description"></a>Açıklamayı Değiştir

' Deki [güvenlik açıklarına](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) bağlı olarak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , aşağıdaki yöntemler artık kullanımdan kalkmıştır ve kimliğiyle derleme zamanı uyarısı oluşturur `SYSLIB0011` . Ayrıca, ASP.NET Core 5,0 ve üzeri uygulamalarda, <xref:System.NotSupportedException> Web uygulaması yeniden etkin işlevselliğe sahip olmadığı takdirde bir oluşturulur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

Aşağıdaki serileştirme yöntemleri de kullanımdan kalkmıştır ve uyarı üretir `SYSLIB0011` , ancak hiçbir davranış değişikliği yoktur:

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu yöntemler <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , .net ekosistemi içinde kullanımını rüzgar çabalarının bir parçası olarak artık kullanılmıyor olarak işaretlenir.

## <a name="recommended-action"></a>Önerilen eylem

- Kodunuzda kullanmayı durdurun <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> . Bunun yerine, veya kullanmayı düşünün <xref:System.Text.Json.JsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> . Daha fazla bilgi için bkz. [BinaryFormatter Güvenlik Kılavuzu](../../../../standard/serialization/binaryformatter-security-guide.md).

- Derleme zamanı uyarısının geçici olarak görüntülenmesini sağlayabilirsiniz <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> `SYSLIB0011` . Bu seçeneği seçmeden önce kodunuzu riskler için kapsamlı olarak değerlendirmenizi öneririz. Uyarıları basmanın en kolay yolu, bireysel çağrı sitesini `#pragma` yönergeleriyle çevreleyecek.

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  Ayrıca, proje dosyasında uyarıyı da gizleyebilirsiniz.

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  Proje dosyasındaki uyarıyı bastırdığınızda, uyarı projedeki tüm kod dosyaları için bastırılır. Gizleme `SYSLIB0011` , diğer eski API 'ler kullanılarak oluşan uyarıları göstermez.

- ASP.NET uygulamalarında kullanmaya devam etmek için <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , proje dosyasında yeniden etkinleştirebilirsiniz. Ancak bunu yapmak kesinlikle önerilir. Daha fazla bilgi için bkz. [BinaryFormatter Güvenlik Kılavuzu](../../../../standard/serialization/binaryformatter-security-guide.md).

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

Önerilen eylemler hakkında daha fazla bilgi için bkz. [BinaryFormatter kullanımdan çıkarma ve disablement hatalarını çözümleme](../../../../standard/serialization/binaryformatter-security-guide.md).

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET Core

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
