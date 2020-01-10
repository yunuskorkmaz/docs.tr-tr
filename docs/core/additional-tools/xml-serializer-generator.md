---
title: Microsoft XML seri hale getirici Oluşturucusu
description: Microsoft XML seri hale getirici oluşturucusuna genel bakış. Projenizde bulunan türler için bir XML serileştirme derlemesi oluşturmak üzere XML seri hale getirici oluşturucusunu kullanın.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714518"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>.NET Core 'da Microsoft XML serileştirici üreticisini kullanma

Bu öğreticide, bir C# .NET Core UYGULAMASıNDA Microsoft XML serileştirici oluşturucunun nasıl kullanılacağı öğretilir. Bu öğreticinin kursu boyunca şunları öğrenirsiniz:

> [!div class="checklist"]
>
> - .NET Core uygulaması oluşturma
> - Microsoft.XmlSerializer.Generator paketine başvuru ekleme
> - Bağımlılık eklemek için MyApp.csproj dosyanızı düzenleme
> - Sınıf ve XmlSerializer ekleme
> - Uygulamayı derleme ve çalıştırma

.NET Framework için [XML serileştirici Oluşturucu (SGen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) gibi, [Microsoft. XmlSerializer. Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET Standard projelerine eşdeğerdir. <xref:System.Xml.Serialization.XmlSerializer>kullanarak bu türlerin nesnelerini serileştirmek veya seri hale getirmede XML serileştirmesinin başlangıç performansını geliştirmek için bir derlemede bulunan türler için bir XML serileştirme bütünleştirilmiş kodu oluşturur.

## <a name="prerequisites"></a>Prerequisites

Bu öğreticiyi tamamlamak için:

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya üzeri.
- En sevdiğiniz kod düzenleyiciniz.

> [!TIP]
> Bir kod Düzenleyicisi yüklemeniz mı gerekiyor? [Visual Studio 'yu](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)deneyin!

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>.NET Core konsol uygulamasında Microsoft XML serileştirici oluşturucusunu kullanma

Aşağıdaki yönergelerde, bir .NET Core konsol uygulamasında XML serileştirici oluşturucunun nasıl kullanılacağı gösterilmektedir.

### <a name="create-a-net-core-console-application"></a>.NET Core konsol uygulaması oluşturma

Bir komut istemi açın ve *MyApp*adlı bir klasör oluşturun. Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>MyApp projesindeki Microsoft. XmlSerializer. Generator paketine bir başvuru ekleyin

Başvuruyu projenize eklemek için [`dotnet add package`](../tools//dotnet-add-package.md) komutunu kullanın.

Tür:

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Paketi ekledikten sonra MyApp. csproj üzerinde yapılan değişiklikleri doğrulayın

Kod düzenleyicinizi açın ve Haydi başlayın! Uygulamayı geliştirdiğimiz *MyApp* dizininden çalışmaya devam ediyoruz.

Metin düzenleyicinizde *MyApp. csproj* ' yı açın.

[`dotnet add package`](../tools//dotnet-add-package.md) komutunu çalıştırdıktan sonra, *MyApp. csproj* proje dosyanıza aşağıdaki satırlar eklenir:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>.NET Core CLI araç desteği için başka bir ItemGroup bölümü ekleme

İncelenen `ItemGroup` bölümden sonra aşağıdaki satırları ekleyin:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Uygulamaya bir sınıf ekleme

Metin düzenleyicinizde *program.cs* öğesini açın. *Program.cs*içinde *MyClass* adlı sınıfı ekleyin.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>MyClass için `XmlSerializer` oluşturma

MyClass için bir `XmlSerializer` oluşturmak için aşağıdaki satırı *Main* içine ekleyin:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Uygulamayı derleme ve çalıştırma

Hala *MyApp* klasöründe, uygulamayı [`dotnet run`](../tools/dotnet-run.md) aracılığıyla çalıştırın ve çalışma zamanında önceden oluşturulmuş serileştiriciler ' ı otomatik olarak yükler ve kullanır.

Konsol pencerenize aşağıdaki komutu yazın:

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md) , derleme hedeflerinin oluşturulduğundan emin olmak için [`dotnet build`](../tools/dotnet-build.md) çağırır ve sonra hedef uygulamayı çalıştırmak için `dotnet <assembly.dll>` çağırır.

> [!IMPORTANT]
> Uygulamanızı çalıştırmak için bu öğreticide gösterilen komutlar ve adımlar yalnızca geliştirme zamanı sırasında kullanılır. Uygulamanızı dağıtmaya hazırsanız, .NET Core uygulamaları için farklı [dağıtım stratejilerine](../deploying/index.md) ve [`dotnet publish`](../tools/dotnet-publish.md) komutuna göz atın.

Her şey başarılı olursa, çıkış klasöründe *MyApp. Xmlserileştiriciler. dll* adlı bir derleme oluşturulur.

Tebrikler! Yalnızca şunları yapın:
> [!div class="checklist"]
>
> - .NET Core uygulaması oluşturuldu.
> - Microsoft. XmlSerializer. Generator paketine bir başvuru eklendi.
> - Bağımlılıklar eklemek için MyApp. csproj dosyanızı düzenlendi.
> - Bir sınıf ve XmlSerializer eklendi.
> - Uygulamayı oluşturulup çalıştırdık.

## <a name="related-resources"></a>İlgili kaynaklar

- [XML Serileştirmeye Giriş](../../standard/serialization/introducing-xml-serialization.md)
- [XmlSerializer (C#) kullanarak serileştirme](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [Nasıl yapılır: XmlSerializer kullanarak serileştirme (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
