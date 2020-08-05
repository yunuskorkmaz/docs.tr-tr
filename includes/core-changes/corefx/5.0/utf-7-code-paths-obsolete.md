---
ms.openlocfilehash: 1cb6e953aa57c72ee6a2665c521bada10e0786cf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455763"
---
### <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="45c48-101">UTF-7 kod yolları artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="45c48-101">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="45c48-102">UTF-7 kodlaması artık uygulamalar arasında geniş bir kullanım değildir ve birçok adım artık değişim içinde [kullanımını](https://security.stackexchange.com/a/68609/3573) dengeler.</span><span class="sxs-lookup"><span data-stu-id="45c48-102">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="45c48-103">Ayrıca, UTF-7 kodlu verilerle karşılaşmayı düşünmeyin uygulamalarda [saldırı vektörü olarak da kullanılır](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) .</span><span class="sxs-lookup"><span data-stu-id="45c48-103">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="45c48-104">Microsoft, <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> hata algılaması sağlamadığı için kullanımını uyarır.</span><span class="sxs-lookup"><span data-stu-id="45c48-104">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="45c48-105">Sonuç olarak, <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> özellik ve <xref:System.Text.UTF7Encoding.%23ctor%2A> oluşturucular artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="45c48-105">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="45c48-106">Ayrıca, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> ve <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> artık belirtmenize izin vermez `UTF-7` .</span><span class="sxs-lookup"><span data-stu-id="45c48-106">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="45c48-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="45c48-107">Change description</span></span>

<span data-ttu-id="45c48-108">Daha önce, API 'leri kullanarak UTF-7 kodlamasının bir örneğini oluşturabilirsiniz <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="45c48-108">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="45c48-109">Örnek:</span><span class="sxs-lookup"><span data-stu-id="45c48-109">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="45c48-110">Ayrıca, UTF-7 kodlamasını temsil eden bir örnek, <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> , sistemde kayıtlı tüm örnekleri numaralandırır yöntemi tarafından numaralandırılır <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="45c48-110">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="45c48-111">.NET 5,0 ' den başlayarak, <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> özellik ve <xref:System.Text.UTF7Encoding.%23ctor%2A> oluşturucular kullanımdan kalkmıştır ve uyarı `SYSLIB0001` (veya `MSLIB0001` önizleme sürümlerinde) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45c48-111">Starting in .NET 5.0, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="45c48-112">Ancak, bir sınıfı kullanırken çağıranların aldığı uyarı sayısını azaltmak için <xref:System.Text.UTF7Encoding> <xref:System.Text.UTF7Encoding> türün kendisi kullanılmıyor olarak işaretlenmez.</span><span class="sxs-lookup"><span data-stu-id="45c48-112">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="45c48-113">Ayrıca, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> Yöntemler kodlama adını `utf-7` ve kod sayfasını `65000` olarak değerlendirir `unknown` .</span><span class="sxs-lookup"><span data-stu-id="45c48-113">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="45c48-114">Kodlama olarak davranması `unknown` metodun bir oluşturmasına neden olur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="45c48-114">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="45c48-115">Son olarak, <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> Yöntem döndürdüğü DIZIDE UTF-7 kodlamasını içermez <xref:System.Text.EncodingInfo> .</span><span class="sxs-lookup"><span data-stu-id="45c48-115">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="45c48-116">Kod örneği oluşturulamıyor çünkü örneklenemez.</span><span class="sxs-lookup"><span data-stu-id="45c48-116">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

#### <a name="reason-for-change"></a><span data-ttu-id="45c48-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="45c48-117">Reason for change</span></span>

<span data-ttu-id="45c48-118">Birçok uygulama `Encoding.GetEncoding("encoding-name")` , güvenilmeyen bir kaynak tarafından sağlanmış bir kodlama adı değeriyle çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="45c48-118">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="45c48-119">Örneğin, bir Web istemcisi veya sunucu `charset` üstbilginin bölümünü alabilir `Content-Type` ve değeri doğrulamadan doğrudan öğesine geçirebilir `Encoding.GetEncoding` .</span><span class="sxs-lookup"><span data-stu-id="45c48-119">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="45c48-120">Bu, kötü amaçlı bir uç noktanın belirtilmesine izin verebilir, bu da `Content-Type: ...; charset=utf-7` alıcı uygulamanın hatalı davranmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="45c48-120">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="45c48-121">Ayrıca, UTF-7 kod yollarının devre dışı bırakılması, Blazor tarafından kullanılanlar gibi derleyicilerin en iyi duruma getirilmesi için, bu kod yollarını elde eden uygulamadan tamamen kaldırır.</span><span class="sxs-lookup"><span data-stu-id="45c48-121">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="45c48-122">Sonuç olarak, derlenen uygulamalar daha verimli bir şekilde çalışır ve daha az disk alanı kaplar.</span><span class="sxs-lookup"><span data-stu-id="45c48-122">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="45c48-123">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="45c48-123">Version introduced</span></span>

<span data-ttu-id="45c48-124">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="45c48-124">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="45c48-125">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="45c48-125">Recommended action</span></span>

<span data-ttu-id="45c48-126">Çoğu durumda, herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="45c48-126">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="45c48-127">Ancak, daha önce UTF-7 ile ilgili kod yollarını etkinleştiren uygulamalar için aşağıdaki kılavuzu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="45c48-127">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="45c48-128">Uygulamanız <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> Güvenilmeyen bir kaynak tarafından belirtilen bilinmeyen kodlama adlarıyla çağrılıyordu:</span><span class="sxs-lookup"><span data-stu-id="45c48-128">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="45c48-129">Bunun yerine, kodlama adlarını yapılandırılabilir bir izin verilenler listesiyle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="45c48-129">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="45c48-130">Yapılandırılabilir izin verilenler listesi en azından endüstri standardı "UTF-8" i içermelidir.</span><span class="sxs-lookup"><span data-stu-id="45c48-130">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="45c48-131">İstemcileriniz ve mevzuata gereksinimlerinize bağlı olarak, "GB18030" gibi bölgeye özgü kodlamalar de izin vermeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="45c48-131">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="45c48-132">Bir izin verilenler listesi gerçekleştirmezseniz, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> <xref:System.Text.Encoding> sisteme yerleştirilmiş olan veya özel bir ile kaydedilmiş herhangi birini döndürür <xref:System.Text.EncodingProvider> .</span><span class="sxs-lookup"><span data-stu-id="45c48-132">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="45c48-133">Hizmetin gereksinimlerini, bu durumun istenen davranış olduğunu doğrulamak için denetleyin.</span><span class="sxs-lookup"><span data-stu-id="45c48-133">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="45c48-134">, Uygulamanız bu makalede daha sonra bahsedilen uyumluluk anahtarını yeniden etkinleştirmediği takdirde UTF-7 varsayılan olarak devre dışı olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="45c48-134">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="45c48-135"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>Ya da <xref:System.Text.UTF7Encoding> kendi protokolde veya dosya biçimindeyse kullanıyorsanız:</span><span class="sxs-lookup"><span data-stu-id="45c48-135">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="45c48-136">Veya kullanarak geçiş <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> yapın <xref:System.Text.UTF8Encoding> .</span><span class="sxs-lookup"><span data-stu-id="45c48-136">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="45c48-137">UTF-8 endüstri standardıdır ve diller, işletim sistemleri ve çalışma zamanları genelinde yaygın olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="45c48-137">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="45c48-138">UTF-8 kullanımı, kodunuzun gelecekteki bakımını kolaylaştırır ve ekosisteminin geri kalanı ile daha birlikte çalışabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="45c48-138">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="45c48-139">Bir örneği karşılaştırıyorsanız <xref:System.Text.Encoding> <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="45c48-139">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="45c48-140">Bunun yerine, iyi bilinen UTF-7 kod sayfasına karşı bir denetim gerçekleştirmeyi göz önünde bulundurun `65000` .</span><span class="sxs-lookup"><span data-stu-id="45c48-140">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="45c48-141">Kod sayfasıyla karşılaştırıldığında, uyarıyı önleyin ve aynı zamanda türü bir veya alt sınıfı olarak çağırırın gibi bazı uç durumları da idare edersiniz `new UTF7Encoding()` .</span><span class="sxs-lookup"><span data-stu-id="45c48-141">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

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

- <span data-ttu-id="45c48-142">Veya kullanmanız gerekiyorsa <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding> :</span><span class="sxs-lookup"><span data-stu-id="45c48-142">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="45c48-143">`SYSLIB0001`Koddaki veya projenizin *. csproj* dosyasının içindeki uyarıyı gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45c48-143">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

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
  > <span data-ttu-id="45c48-144">Gizleme `SYSLIB0001` yalnızca ve kullanımdan kaldırma uyarılarını devre dışı bırakır <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding> .</span><span class="sxs-lookup"><span data-stu-id="45c48-144">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="45c48-145">Diğer uyarıları devre dışı bırakır veya gibi API 'lerin davranışını değiştirmez <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="45c48-145">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="45c48-146">Şunları desteketmeniz gerekirse `Encoding.GetEncoding("utf-7", ...)` :</span><span class="sxs-lookup"><span data-stu-id="45c48-146">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="45c48-147">Bir uyumluluk anahtarı aracılığıyla bunun desteğini yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45c48-147">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="45c48-148">Bu uyumluluk anahtarı, aşağıdaki örneklerde gösterildiği gibi uygulamanın *. csproj* dosyasında veya bir [çalışma zamanı yapılandırma dosyasında](../../../../docs/core/run-time-config/index.md)belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="45c48-148">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../../docs/core/run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="45c48-149">Uygulamanın *. csproj* dosyasında:</span><span class="sxs-lookup"><span data-stu-id="45c48-149">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="45c48-150">Uygulamanın dosyada *runtimeconfig.template.js* :</span><span class="sxs-lookup"><span data-stu-id="45c48-150">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="45c48-151">UTF-7 desteğini yeniden etkinleştirirseniz, çağıran kod için bir güvenlik incelemesi gerçekleştirmelisiniz <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="45c48-151">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="45c48-152">Kategori</span><span class="sxs-lookup"><span data-stu-id="45c48-152">Category</span></span>

- <span data-ttu-id="45c48-153">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="45c48-153">Core .NET libraries</span></span>
- <span data-ttu-id="45c48-154">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="45c48-154">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="45c48-155">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="45c48-155">Affected APIs</span></span>

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
