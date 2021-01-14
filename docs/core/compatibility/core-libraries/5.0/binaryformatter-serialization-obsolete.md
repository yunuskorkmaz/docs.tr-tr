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
# <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a><span data-ttu-id="8af62-103">BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış</span><span class="sxs-lookup"><span data-stu-id="8af62-103">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>

<span data-ttu-id="8af62-104">`Serialize` ve, `Deserialize` <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , ve üzerindeki yöntemleri <xref:System.Runtime.Serialization.Formatter> <xref:System.Runtime.Serialization.IFormatter> artık uyarı olarak kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="8af62-104">`Serialize` and `Deserialize` methods on <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter>, and <xref:System.Runtime.Serialization.IFormatter> are now obsolete as warning.</span></span> <span data-ttu-id="8af62-105">Ayrıca, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ASP.NET uygulamaları için serileştirme varsayılan olarak yasaktır.</span><span class="sxs-lookup"><span data-stu-id="8af62-105">Additionally, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is prohibited by default for ASP.NET apps.</span></span>

## <a name="change-description"></a><span data-ttu-id="8af62-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="8af62-106">Change description</span></span>

<span data-ttu-id="8af62-107">' Deki [güvenlik açıklarına](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) bağlı olarak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , aşağıdaki yöntemler artık kullanımdan kalkmıştır ve kimliğiyle derleme zamanı uyarısı oluşturur `SYSLIB0011` .</span><span class="sxs-lookup"><span data-stu-id="8af62-107">Due to [security vulnerabilities](../../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following methods are now obsolete and produce a compile-time warning with ID `SYSLIB0011`.</span></span> <span data-ttu-id="8af62-108">Ayrıca, ASP.NET Core 5,0 ve üzeri uygulamalarda, <xref:System.NotSupportedException> Web uygulaması yeniden etkin işlevselliğe sahip olmadığı takdirde bir oluşturulur <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .</span><span class="sxs-lookup"><span data-stu-id="8af62-108">Additionally, in ASP.NET Core 5.0 and later apps, they will throw a <xref:System.NotSupportedException>, unless the web app has re-enabled <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> functionality.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

<span data-ttu-id="8af62-109">Aşağıdaki serileştirme yöntemleri de kullanımdan kalkmıştır ve uyarı üretir `SYSLIB0011` , ancak hiçbir davranış değişikliği yoktur:</span><span class="sxs-lookup"><span data-stu-id="8af62-109">The following serialization methods are also obsolete and produce warning `SYSLIB0011`, but have no behavioral changes:</span></span>

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="version-introduced"></a><span data-ttu-id="8af62-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="8af62-110">Version introduced</span></span>

<span data-ttu-id="8af62-111">5.0</span><span class="sxs-lookup"><span data-stu-id="8af62-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8af62-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="8af62-112">Reason for change</span></span>

<span data-ttu-id="8af62-113">Bu yöntemler <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , .net ekosistemi içinde kullanımını rüzgar çabalarının bir parçası olarak artık kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="8af62-113">These methods are marked obsolete as part of an effort to wind down usage of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> within the .NET ecosystem.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8af62-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="8af62-114">Recommended action</span></span>

- <span data-ttu-id="8af62-115">Kodunuzda kullanmayı durdurun <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .</span><span class="sxs-lookup"><span data-stu-id="8af62-115">Stop using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in your code.</span></span> <span data-ttu-id="8af62-116">Bunun yerine, veya kullanmayı düşünün <xref:System.Text.Json.JsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8af62-116">Instead, consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="8af62-117">Daha fazla bilgi için bkz. [BinaryFormatter Güvenlik Kılavuzu](../../../../standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="8af62-117">For more information, see [BinaryFormatter security guide](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

- <span data-ttu-id="8af62-118">Derleme zamanı uyarısının geçici olarak görüntülenmesini sağlayabilirsiniz <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> `SYSLIB0011` .</span><span class="sxs-lookup"><span data-stu-id="8af62-118">You can temporarily suppress the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> compile-time warning, which is `SYSLIB0011`.</span></span> <span data-ttu-id="8af62-119">Bu seçeneği seçmeden önce kodunuzu riskler için kapsamlı olarak değerlendirmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="8af62-119">We recommend that you thoroughly assess your code for risks before choosing this option.</span></span> <span data-ttu-id="8af62-120">Uyarıları basmanın en kolay yolu, bireysel çağrı sitesini `#pragma` yönergeleriyle çevreleyecek.</span><span class="sxs-lookup"><span data-stu-id="8af62-120">The easiest way to suppress the warnings is to surround the individual call site with `#pragma` directives.</span></span>

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

  <span data-ttu-id="8af62-121">Ayrıca, proje dosyasında uyarıyı da gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8af62-121">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  <span data-ttu-id="8af62-122">Proje dosyasındaki uyarıyı bastırdığınızda, uyarı projedeki tüm kod dosyaları için bastırılır.</span><span class="sxs-lookup"><span data-stu-id="8af62-122">If you suppress the warning in the project file, the warning is suppressed for all code files in the project.</span></span> <span data-ttu-id="8af62-123">Gizleme `SYSLIB0011` , diğer eski API 'ler kullanılarak oluşan uyarıları göstermez.</span><span class="sxs-lookup"><span data-stu-id="8af62-123">Suppressing `SYSLIB0011` does not suppress warnings caused by using other obsolete APIs.</span></span>

- <span data-ttu-id="8af62-124">ASP.NET uygulamalarında kullanmaya devam etmek için <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , proje dosyasında yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8af62-124">To continue using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in ASP.NET apps, you can re-enable it in the project file.</span></span> <span data-ttu-id="8af62-125">Ancak bunu yapmak kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="8af62-125">However, it's strongly recommended not to do this.</span></span> <span data-ttu-id="8af62-126">Daha fazla bilgi için bkz. [BinaryFormatter Güvenlik Kılavuzu](../../../../standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="8af62-126">For more information, see [BinaryFormatter security guide](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

<span data-ttu-id="8af62-127">Önerilen eylemler hakkında daha fazla bilgi için bkz. [BinaryFormatter kullanımdan çıkarma ve disablement hatalarını çözümleme](../../../../standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="8af62-127">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](../../../../standard/serialization/binaryformatter-security-guide.md).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8af62-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8af62-128">Affected APIs</span></span>

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
