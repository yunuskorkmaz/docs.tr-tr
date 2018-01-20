---
title: ".NET Core üzerinde Microsoft XML seri hale getirici oluşturucusunu kullanarak"
description: "Microsoft XML seri hale getirici Oluşturucu genel bakış."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 4b838cafe1f4835c1c5aa6086c0997a4a9e39a9e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>.NET Core üzerinde Microsoft XML seri hale getirici oluşturucusunu kullanarak

Bu öğretici bir C# .NET Core uygulamasında Microsoft XML seri hale getirici Oluşturucu kullanmayı öğretir. Bu öğreticinin sürecinde size bilgi edinin:

> [!div class="checklist"]
> * .NET Core uygulaması oluşturma
> * Microsoft.XmlSerializer.Generator paketine başvuru ekleme
> * Bağımlılıkları eklemek için MyApp.csproj düzenleme
> * Bir sınıf ve XmlSerializer ekleme
> * Derleme ve uygulamayı çalıştırma 

Gibi [Xml seri hale getirici Oluşturucu (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET standart projeleri için eşdeğerdir. XML serileştirme bütünleştirilmiş serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede bulunan türleri için oluşturduğu <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi tamamlamak için:

* Yükleme [.NET Core SDK 2.1.3 veya daha yenisi](https://www.microsoft.com/net/download)
* Henüz yapmadıysanız, sık kullanılan kod düzenleyicisinde yükleyin.

> [!TIP]
> Kod Düzenleyicisi yüklemeniz gerekiyor? Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Microsoft XML seri hale getirici oluşturucuyu bir .NET Core konsol uygulamasında kullanma 

Aşağıdaki yönergeler XML seri hale getirici oluşturucuyu bir .NET Core konsol uygulamasında kullanmayı gösterir.

### <a name="create-a-net-core-console-application"></a>Bir .NET Core konsol uygulaması oluşturun

Bir komut istemi açın ve adlı bir klasör oluşturun *Uygulamam*. Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Uygulamam projesinde Microsoft.XmlSerializer.Generator paketine bir başvuru ekleyin

Kullanım [ `dotnet add package` ](../tools//dotnet-add-package.md) başvuru projenize eklemek için komutu. 

Tür:
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Paket eklendikten sonra MyApp.csproj değişiklikleri doğrulayın

Kod Düzenleyicisi'ni açın ve başlayalım! Hala gelen çalışıyoruz *Uygulamam* biz yerleşik uygulama dizini.

Açık *MyApp.csproj* metin düzenleyicinizde.

Çalıştırdıktan sonra [ `dotnet add package` ](../tools//dotnet-add-package.md) komutu, aşağıdaki satırları eklenir, *MyApp.csproj* proje dosyası:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>.NET Core CLI aracı desteği için başka bir ItemGroup Bölüm Ekle
 
 Sonra aşağıdaki satırları ekleyin `ItemGroup` biz Denetlenmekte bölümü:
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a>Uygulamada bir sınıf ekleyin

Açık *Program.cs* metin düzenleyicinizde. Adlı sınıf ekleme *MyClass* içinde *Program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Oluşturma bir `XmlSerializer` MyClass için

İçinde aşağıdaki satırı ekleyin *ana* oluşturmak için bir `XmlSerializer` MyClass için:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Derleme ve uygulamayı çalıştırma

İçinde hala *Uygulamam* klasörü aracılığıyla uygulamayı çalıştırın, [ `dotnet run` ](../tools/dotnet-run.md) ve otomatik olarak yükler ve çalışma zamanında önceden oluşturulmuş serileştiricileri kullanır.

Konsol penceresinde aşağıdaki komutu yazın:

 ```console
 $ dotnet run
 ```
> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)çağrıları [ `dotnet build` ](../tools/dotnet-build.md) hedefleri yerleşik yapı ve çağrıları emin olmak için `dotnet <assembly.dll>` hedef uygulamayı çalıştırın.

> [!IMPORTANT]
> Komutlar ve uygulamanızı çalıştırmak için Bu öğreticide gösterilen adımlar yalnızca geliştirme zamanı sırasında kullanılır. Uygulamanızı dağıtmak hazır olduğunuzda, farklı bir göz atalım [dağıtım stratejilerini](../deploying/index.md) .NET Core uygulamaları için ve [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.

Her şeyi başarılı olursa, adlı bir derleme *MyApp.XmlSerializers.dll* çıkış klasöründe oluşturulur. 



Tebrikler! yalnızca gerekir:
> [!div class="checklist"]
> * Bir .NET oluşturulan çekirdek uygulama.
> * Microsoft.XmlSerializer.Generator paketine bir başvuru eklenir.
> * Bağımlılıkları eklemek için MyApp.csproj düzenlenemez.
> * Bir sınıf ve XmlSerializer eklendi.
> * Yerleşik ve uygulama çalıştırılmıştır. 

## <a name="related-resources"></a>İlgili Kaynaklar

* [XML Serileştirmeye Giriş](../../standard/serialization/introducing-xml-serialization.md)
* [Nasıl yapılır: XmlSerializer (C#) kullanarak serileştirme](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)
* [Nasıl yapılır: XmlSerializer (Visual Basic) kullanarak serileştirme](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)