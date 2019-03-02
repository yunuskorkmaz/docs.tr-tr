---
title: Microsoft XML serileştirici Oluşturucusu
description: Microsoft XML seri hale getirici oluşturucunun bir genel bakış. XML seri hale getirici oluşturucunun bir XML serileştirme derleme projenizde yer alan türleri oluşturmak için kullanın.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: e5b41b6e5d747cd99a80930bb64e36839af4ab66
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211903"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Microsoft XML seri hale getirici oluşturucunun üzerinde .NET Core kullanma

Bu öğreticide, Microsoft XML seri hale getirici oluşturucunun kullanılacağını öğretir bir C# .NET Core uygulaması. Bu öğreticinin Kurs sırasında şunları öğrenirsiniz:

> [!div class="checklist"]
> * .NET Core uygulaması oluşturma
> * Microsoft.XmlSerializer.Generator paketine bir başvuru ekleme
> * Bağımlılıklar eklemek için MyApp.csproj düzenleme
> * Bir sınıf ve XmlSerializer ekleme
> * Nasıl uygulaması derleme ve çalıştırma

Gibi [Xml seri hale getirici oluşturucunun (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketini](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) için .NET Core ve .NET Standard projelerine eşdeğerdir. Bir XML serileştirme derleme türleri serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede yer alan oluşturur <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

* [.NET core 2.1 SDK](https://www.microsoft.com/net/download) veya üzeri
* Sık kullandığınız kod düzenleyici.

> [!TIP]
> Bir kod Düzenleyicisi'ni yüklemeniz gerekir? Deneyin [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Microsoft XML seri hale getirici oluşturucunun bir .NET Core konsol uygulamasında kullanma

Aşağıdaki yönergeler, XML seri hale getirici oluşturucunun bir .NET Core konsol uygulamasında kullanmayı gösterir.

### <a name="create-a-net-core-console-application"></a>Bir .NET Core konsol uygulaması oluşturun

Bir komut istemi açın ve adlı bir klasör oluşturun *MyApp*. Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Uygulamam projesinde Microsoft.XmlSerializer.Generator paketine bir başvuru ekleyin

Kullanım [ `dotnet add package` ](../tools//dotnet-add-package.md) projenize başvuru eklemek için komutu.

Tür:

```console
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Paket ekledikten sonra değişiklikleri MyApp.csproj doğrulayın

Kod Düzenleyicisi'ni açın ve başlayalım! Hala gelen çalışıyoruz *MyApp* dizin içinde bir uygulama oluşturduk.

Açık *MyApp.csproj* metin düzenleyicinizde.

Çalıştırdıktan sonra [ `dotnet add package` ](../tools//dotnet-add-package.md) komutu aşağıdaki satırları eklenir, *MyApp.csproj* proje dosyası:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>.NET Core CLI aracı desteği için başka bir ItemGroup bölümü ekleyin

Sonra aşağıdaki satırları ekleyin `ItemGroup` biz inceledi bölümü:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Uygulamada bir sınıf ekleyin

Açık *Program.cs* metin düzenleyicinizde. Adlı bir sınıf ekleyin *MyClass* içinde *Program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Oluşturma bir `XmlSerializer` MyClass için

Aşağıdaki satırı ekleyin *ana* oluşturmak için bir `XmlSerializer` MyClass için:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Uygulaması derleme ve çalıştırma

Yine de içinde *MyApp* aracılığıyla uygulamayı çalıştırın, klasör [ `dotnet run` ](../tools/dotnet-run.md) ve otomatik olarak yükler ve seri hale getiricileri genişletme önceden oluşturulan çalışma zamanında kullanır.

Konsol pencerenizde aşağıdaki komutu yazın:

```console
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) hedefleri oluşturulan derleme ve çağrıları emin olmak için `dotnet <assembly.dll>` hedef uygulamayı çalıştırın.

> [!IMPORTANT]
> Komutlar ve uygulamanızı çalıştırmak için Bu öğreticide gösterilen adımlar yalnızca geliştirme zamanı sırasında kullanılır. Uygulamanızı dağıtmak hazır olduğunuzda, farklı bir göz atın [dağıtım stratejilerini](../deploying/index.md) .NET Core uygulamaları için ve [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.

Her şeyi başarılı olursa, adında bir derleme *MyApp.XmlSerializers.dll* çıktı klasöründe oluşturulur.

Tebrikler! yalnızca gerekir:
> [!div class="checklist"]
> * Oluşturulan bir .NET Core uygulaması.
> * Microsoft.XmlSerializer.Generator paketine bir başvuru eklenir.
> * Bağımlılıklar eklemek için MyApp.csproj düzenlendi.
> * Bir sınıf ve XmlSerializer eklendi.
> * Yerleşik ve uygulamayı çalıştırdınız.

## <a name="related-resources"></a>İlgili kaynaklar

* [XML Serileştirmeye Giriş](../../standard/serialization/introducing-xml-serialization.md)
* [Nasıl yapılır: XmlSerializer kullanarak serileştirme (C#)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [Nasıl yapılır: XmlSerializer (Visual Basic) kullanarak seri hale getirme](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)