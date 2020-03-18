---
title: Microsoft XML Serializer Jeneratör
description: Microsoft XML Serializer Generator'a genel bakış. Projenizde bulunan türler için bir XML serileştirme derlemesi oluşturmak için XML Serializer Generator'ı kullanın.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714518"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Microsoft XML Serializer Generator'ı .NET Core'da kullanma

Bu öğretici, C# .NET Core uygulamasında Microsoft XML Serializer Generator'ı nasıl kullanacağınızı öğretir. Bu öğretici sırasında, öğrenmek:

> [!div class="checklist"]
>
> - .NET Core uygulaması oluşturma
> - Microsoft.XmlSerializer.Generator paketine başvuru ekleme
> - Bağımlılık eklemek için MyApp.csproj dosyanızı düzenleme
> - Sınıf ve XmlSerializer ekleme
> - Uygulamayı derleme ve çalıştırma

.NET Framework için [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) gibi, [Microsoft.XmlSerializer.Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) de .NET Core ve .NET Standard projelerine eşdeğerdir. Bu, bu tür nesneleri serihale veya de-serializing nesneleri kullanırken XML serileştirme başlangıç performansını artırmak için bir <xref:System.Xml.Serialization.XmlSerializer>derleme de bulunan türleri için bir XML serileştirme derlemesi oluşturur.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) veya sonrası.
- En sevdiğin kod düzenleyicisi.

> [!TIP]
> Bir kod düzenleyicisi yüklemeniz mi gerekiyor? [Visual Studio'yı](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)deneyin!

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Microsoft XML Serializer Generator'ı .NET Core konsol uygulamasında kullanma

Aşağıdaki yönergeler, .NET Core konsol uygulamasında XML Serializer Generator'ı nasıl kullanacağınızı gösterir.

### <a name="create-a-net-core-console-application"></a>.NET Core konsol uygulaması oluşturma

Komut istemini açın ve *MyApp*adında bir klasör oluşturun. Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>MyApp projesinde Microsoft.XmlSerializer.Generator paketine başvuru ekleme

Projenize [`dotnet add package`](../tools//dotnet-add-package.md) başvuru eklemek için komutu kullanın.

Şunu yazın:

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Paketi ekledikten sonra MyApp.csproj'daki değişiklikleri doğrulayın

Kod düzenleyicinizi açın ve başlayalım! Uygulamayı oluşturduğumuz *MyApp* dizininden çalışmaya devam ediyoruz.

Metin editörünüzde *MyApp.csproj'u* açın.

Komutu [`dotnet add package`](../tools//dotnet-add-package.md) çalıştırdıktan sonra *MyApp.csproj* proje dosyanıza aşağıdaki satırlar eklenir:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>.NET Core CLI Aracı desteği için başka bir ItemGroup bölümü ekleme

İncelediğimiz bölümden `ItemGroup` sonra aşağıdaki satırları ekleyin:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Uygulamada sınıf ekleme

Metin düzenleyicinizde *Program.cs* açın. myclass adlı *MyClass* sınıfı *Program.cs'da*ekleyin.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>MyClass `XmlSerializer` için bir oluşturma

MyClass için bir satır `XmlSerializer` oluşturmak için *Main'in* içine aşağıdaki satırı ekleyin:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Uygulamayı derleme ve çalıştırma

MyApp *MyApp* klasöründe hala uygulamayı çalıştırın [`dotnet run`](../tools/dotnet-run.md) ve otomatik olarak yüklenir ve çalışma zamanında önceden oluşturulmuş serializer'leri kullanır.

Konsol pencerenize aşağıdaki komutu yazın:

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)yapı [`dotnet build`](../tools/dotnet-build.md) hedeflerinin oluşturulup, hedef uygulamayı çalıştırmak `dotnet <assembly.dll>` için çağrıda bulunulmasını sağlar.

> [!IMPORTANT]
> Uygulamanızı çalıştırmak için bu öğreticide gösterilen komutlar ve adımlar yalnızca geliştirme süresi boyunca kullanılır. Uygulamanızı dağıtmaya hazır olduğunuzda,.NET Core uygulamaları ve komutu için farklı [`dotnet publish`](../tools/dotnet-publish.md) [dağıtım stratejilerine](../deploying/index.md) göz atın.

Her şey başarılı olursa, çıkış klasöründe *MyApp.XmlSerializers.dll* adında bir derleme oluşturulur.

Tebrikler! Sadece var:
> [!div class="checklist"]
>
> - Bir .NET Core uygulaması oluşturuldu.
> - Microsoft.XmlSerializer.Generator paketine bir başvuru eklendi.
> - Bağımlılıkları eklemek için MyApp.csproj'unuzu düzenlediniz.
> - Bir sınıf ve xmlSerializer eklendi.
> - Uygulamayı oluşturup çalıştırın.

## <a name="related-resources"></a>İlgili kaynaklar

- [XML Serileştirmeye Giriş](../../standard/serialization/introducing-xml-serialization.md)
- [XmlSerializer (C#) kullanarak serileştirme](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [Nasıl yapılır: XmlSerializer kullanarak Serialize (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
