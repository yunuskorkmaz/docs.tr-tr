---
description: C# derleyici seçenekleri. C# derleyicisinin davranışını denetleyen seçenekleri öğrenin.
title: C# Derleyici Seçenekleri
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: e9fc2fccdb48ab8646cdbf02db14b6ec1b9842df
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881165"
---
# <a name="c-compiler-options"></a>C# Derleyici Seçenekleri

Bu bölümde, C# derleyicisi tarafından yorumlanan seçenekler açıklanmaktadır. .NET projelerinde derleyici seçeneklerini ayarlamak için iki farklı yol vardır:

- ***\* . Csproj dosyanızda seçeneği belirtin***: *\* . csproj* DOSYANıZDAKI herhangi bir derleyici seçeneği için XML öğeleri ekleyebilirsiniz. Öğe adı, derleyici seçeneği ile aynıdır. XML öğesinin değeri, derleyici seçeneğinin değerini ayarlar. Proje dosyalarındaki seçenekleri ayarlama hakkında daha fazla bilgi için [.NET SDK projeleri Için MSBuild özellikleri](../../../core/project-sdk/msbuild-props.md)makalesine bakın.
- ***Visual Studio özellik sayfalarını kullanma***: Visual Studio yapı özelliklerini düzenlemek için özellik sayfaları sağlar. Bunlar hakkında daha fazla bilgi edinmek için bkz. [Proje ve çözüm özelliklerini yönetme-Windows](/visualstudio/ide/managing-project-and-solution-properties#c-visual-basic-and-f-projects) veya [Proje ve çözüm özelliklerini yönetme-Mac](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="net-framework-projects"></a>.NET Framework projeleri

> [!IMPORTANT]
> Bu bölüm yalnızca .NET Framework projelerine yöneliktir.

Yukarıda açıklanan mekanizmaların yanı sıra, .NET Framework projeleri için iki ek yöntem kullanarak derleyici seçeneklerini ayarlayabilirsiniz:

- **.NET Framework projeler Için komut satırı bağımsız değişkenleri**: .NET Framework projeleri  , `dotnet build` Proje derlemek için yerinecsc.exekullanır. .NET Framework projeleri için *csc.exe* komut satırı bağımsız değişkenlerini belirtebilirsiniz.
- **Derlenen ASP.NET sayfaları**: .NET Framework projeler, sayfaları derlemek için *web.config* dosyasının bir bölümünü kullanır. Yeni derleme sistemi için ASP.NET Core projeler, Seçenekler proje dosyasından alınır.

Bazı derleyici seçenekleri için Word *csc.exe* ve .NET Framework projelerinden yeni MSBuild sistemine değişmiştir. Bu bölümün tamamında yeni sözdizimi kullanılır. Her iki sürüm de her sayfanın üst kısmında listelenir. *csc.exe* için, herhangi bir bağımsız değişken seçeneğinin ve iki nokta üst üste işaretinden sonra listelenir. Örneğin, bu `-doc` seçenek şöyle olacaktır:

```console
-doc:DocFile.xml
```

Komut istemine yürütülebilir dosyasının adını (*csc.exe*) yazarak C# derleyicisini çağırabilirsiniz.

.NET Framework projeler için komut satırından da *csc.exe* çalıştırabilirsiniz. Her derleyici seçeneği iki biçimde mevcuttur: **-Option** ve **/Option**. .NET Framework web projelerinde, *web.config* dosyasında arka plan kodu derleme seçeneklerini belirtirsiniz. Daha fazla bilgi için bkz. [ \<compiler> öğesi](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).

**Visual Studio için geliştirici komut istemi** kullanıyorsanız, tüm gerekli ortam değişkenleri sizin için ayarlanır. Bu araca erişme hakkında daha fazla bilgi için bkz. [Visual Studio için geliştirici komut istemi](/visualstudio/ide/reference/command-prompt-powershell).

*csc.exe* yürütülebilir dosya genellikle \\ *\<Version>* *Windows* dizini altındaki Microsoft. NET\Framework klasöründe bulunur. Bu dosyanın yeri, belirli bir bilgisayarın tam yapılandırmasına bağlı olarak değişebilir. Bilgisayarınızda birden fazla .NET Framework sürümü yüklüyse, bu dosyanın birden çok sürümünü bulabilirsiniz. Bu tür yüklemeler hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).
