---
ms.openlocfilehash: 1cb6e953aa57c72ee6a2665c521bada10e0786cf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455763"
---
### <a name="utf-7-code-paths-are-obsolete"></a>UTF-7 kod yolları artık kullanılmıyor

UTF-7 kodlaması artık uygulamalar arasında geniş bir kullanım değildir ve birçok adım artık değişim içinde [kullanımını](https://security.stackexchange.com/a/68609/3573) dengeler. Ayrıca, UTF-7 kodlu verilerle karşılaşmayı düşünmeyin uygulamalarda [saldırı vektörü olarak da kullanılır](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) . Microsoft, <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> hata algılaması sağlamadığı için kullanımını uyarır.

Sonuç olarak, <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> özellik ve <xref:System.Text.UTF7Encoding.%23ctor%2A> oluşturucular artık kullanılmıyor. Ayrıca, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> ve <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> artık belirtmenize izin vermez `UTF-7` .

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, API 'leri kullanarak UTF-7 kodlamasının bir örneğini oluşturabilirsiniz <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> . Örnek:

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

Ayrıca, UTF-7 kodlamasını temsil eden bir örnek, <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> , sistemde kayıtlı tüm örnekleri numaralandırır yöntemi tarafından numaralandırılır <xref:System.Text.Encoding> .

.NET 5,0 ' den başlayarak, <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> özellik ve <xref:System.Text.UTF7Encoding.%23ctor%2A> oluşturucular kullanımdan kalkmıştır ve uyarı `SYSLIB0001` (veya `MSLIB0001` önizleme sürümlerinde) oluşturur. Ancak, bir sınıfı kullanırken çağıranların aldığı uyarı sayısını azaltmak için <xref:System.Text.UTF7Encoding> <xref:System.Text.UTF7Encoding> türün kendisi kullanılmıyor olarak işaretlenmez.

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

Ayrıca, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> Yöntemler kodlama adını `utf-7` ve kod sayfasını `65000` olarak değerlendirir `unknown` . Kodlama olarak davranması `unknown` metodun bir oluşturmasına neden olur <xref:System.ArgumentException> .

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

Son olarak, <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> Yöntem döndürdüğü DIZIDE UTF-7 kodlamasını içermez <xref:System.Text.EncodingInfo> . Kod örneği oluşturulamıyor çünkü örneklenemez.

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Birçok uygulama `Encoding.GetEncoding("encoding-name")` , güvenilmeyen bir kaynak tarafından sağlanmış bir kodlama adı değeriyle çağrı yapılır. Örneğin, bir Web istemcisi veya sunucu `charset` üstbilginin bölümünü alabilir `Content-Type` ve değeri doğrulamadan doğrudan öğesine geçirebilir `Encoding.GetEncoding` . Bu, kötü amaçlı bir uç noktanın belirtilmesine izin verebilir, bu da `Content-Type: ...; charset=utf-7` alıcı uygulamanın hatalı davranmasına neden olabilir.

Ayrıca, UTF-7 kod yollarının devre dışı bırakılması, Blazor tarafından kullanılanlar gibi derleyicilerin en iyi duruma getirilmesi için, bu kod yollarını elde eden uygulamadan tamamen kaldırır. Sonuç olarak, derlenen uygulamalar daha verimli bir şekilde çalışır ve daha az disk alanı kaplar.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu durumda, herhangi bir işlem yapmanız gerekmez. Ancak, daha önce UTF-7 ile ilgili kod yollarını etkinleştiren uygulamalar için aşağıdaki kılavuzu göz önünde bulundurun.

- Uygulamanız <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> Güvenilmeyen bir kaynak tarafından belirtilen bilinmeyen kodlama adlarıyla çağrılıyordu:

  Bunun yerine, kodlama adlarını yapılandırılabilir bir izin verilenler listesiyle karşılaştırın. Yapılandırılabilir izin verilenler listesi en azından endüstri standardı "UTF-8" i içermelidir. İstemcileriniz ve mevzuata gereksinimlerinize bağlı olarak, "GB18030" gibi bölgeye özgü kodlamalar de izin vermeniz gerekebilir.

  Bir izin verilenler listesi gerçekleştirmezseniz, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> <xref:System.Text.Encoding> sisteme yerleştirilmiş olan veya özel bir ile kaydedilmiş herhangi birini döndürür <xref:System.Text.EncodingProvider> . Hizmetin gereksinimlerini, bu durumun istenen davranış olduğunu doğrulamak için denetleyin. , Uygulamanız bu makalede daha sonra bahsedilen uyumluluk anahtarını yeniden etkinleştirmediği takdirde UTF-7 varsayılan olarak devre dışı olmaya devam eder.

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>Ya da <xref:System.Text.UTF7Encoding> kendi protokolde veya dosya biçimindeyse kullanıyorsanız:

  Veya kullanarak geçiş <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> yapın <xref:System.Text.UTF8Encoding> . UTF-8 endüstri standardıdır ve diller, işletim sistemleri ve çalışma zamanları genelinde yaygın olarak desteklenir. UTF-8 kullanımı, kodunuzun gelecekteki bakımını kolaylaştırır ve ekosisteminin geri kalanı ile daha birlikte çalışabilir hale gelir.

- Bir örneği karşılaştırıyorsanız <xref:System.Text.Encoding> <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :

  Bunun yerine, iyi bilinen UTF-7 kod sayfasına karşı bir denetim gerçekleştirmeyi göz önünde bulundurun `65000` . Kod sayfasıyla karşılaştırıldığında, uyarıyı önleyin ve aynı zamanda türü bir veya alt sınıfı olarak çağırırın gibi bazı uç durumları da idare edersiniz `new UTF7Encoding()` .

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- Veya kullanmanız gerekiyorsa <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding> :

  `SYSLIB0001`Koddaki veya projenizin *. csproj* dosyasının içindeki uyarıyı gizleyebilirsiniz.

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

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
  > Gizleme `SYSLIB0001` yalnızca ve kullanımdan kaldırma uyarılarını devre dışı bırakır <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding> . Diğer uyarıları devre dışı bırakır veya gibi API 'lerin davranışını değiştirmez <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .

- Şunları desteketmeniz gerekirse `Encoding.GetEncoding("utf-7", ...)` :

  Bir uyumluluk anahtarı aracılığıyla bunun desteğini yeniden etkinleştirebilirsiniz. Bu uyumluluk anahtarı, aşağıdaki örneklerde gösterildiği gibi uygulamanın *. csproj* dosyasında veya bir [çalışma zamanı yapılandırma dosyasında](../../../../docs/core/run-time-config/index.md)belirtilebilir.

  Uygulamanın *. csproj* dosyasında:

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  Uygulamanın dosyada *runtimeconfig.template.js* :

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > UTF-7 desteğini yeniden etkinleştirirseniz, çağıran kod için bir güvenlik incelemesi gerçekleştirmelisiniz <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Kategori

- Core .NET kitaplıkları
- Güvenlik

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
