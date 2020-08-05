---
ms.openlocfilehash: c5204e8c80cb737338b053c39083c0cc43786447
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517340"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a>BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış

`Serialize`ve, `Deserialize` <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , ve üzerindeki yöntemleri <xref:System.Runtime.Serialization.Formatter> <xref:System.Runtime.Serialization.IFormatter> artık kullanılmıyor. Ayrıca, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ASP.NET uygulamaları için serileştirme varsayılan olarak yasaktır.

#### <a name="change-description"></a>Açıklamayı Değiştir

' Deki [güvenlik açıklarına](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) bağlı olarak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , aşağıdaki yöntemler artık kullanılmıyor. Ayrıca, ASP.NET 5,0 ve üzeri uygulamalarda, <xref:System.NotSupportedException> Web uygulaması yeniden etkin işlevselliğe sahip olmadığı takdirde bir oluşturulur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

Bu yöntemler <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , .net ekosistemi içinde kullanımını rüzgar çabalarının bir parçası olarak artık kullanılmıyor olarak işaretlenir.

Aşağıdaki serileştirme yöntemleri de artık kullanılmıyor, ancak hiçbir davranış değişikliği yok:

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

- Kodunuzda kullanmayı durdurun <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> . Bunun yerine, veya kullanmayı düşünün <xref:System.Text.Json.JsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> . Daha fazla bilgi için bkz. [BinaryFormatter Güvenlik Kılavuzu](../../../../docs/standard/serialization/binaryformatter-security-guide.md).

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

  Proje dosyasındaki uyarıyı bastırdığınızda, uyarı projedeki tüm kod dosyaları için bastırılır. SYSLIB0011 gizleme, diğer eski API 'Ler kullanılarak oluşan uyarıları göstermez.

- ASP.NET uygulamalarında kullanmaya devam etmek için <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , proje dosyasında yeniden etkinleştirebilirsiniz. Ancak bunu yapmak kesinlikle önerilir. Daha fazla bilgi için bkz. [BinaryFormatter Güvenlik Kılavuzu](../../../../docs/standard/serialization/binaryformatter-security-guide.md).

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

Önerilen eylemler hakkında daha fazla bilgi için bkz. [BinaryFormatter kullanımdan çıkarma ve disablement hatalarını çözümleme](https://aka.ms/binaryformatter).

#### <a name="category"></a>Kategori

- Core .NET kitaplıkları
- ASP.NET

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
