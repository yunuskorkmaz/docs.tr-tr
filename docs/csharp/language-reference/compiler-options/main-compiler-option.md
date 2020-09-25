---
description: -Main (C# derleyici seçenekleri)
title: -Main (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: c27898de2a7cc2f3c01c51f8de1122e81b2233b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194121"
---
# <a name="-main-c-compiler-options"></a>-Main (C# derleyici seçenekleri)

Bu seçenek, birden fazla sınıf bir **Main** yöntemi içeriyorsa programa giriş noktasını içeren sınıfı belirtir.

## <a name="syntax"></a>Söz dizimi

```console
-main:class
```

## <a name="arguments"></a>Bağımsız değişkenler

 `class`  
 **Main** metodunu içeren tür.  
 Belirtilen sınıf adı tam olarak nitelenmiş olmalıdır; sınıfını içeren tam ad alanını ve ardından sınıf adını içermelidir. Örneğin, `Main` yöntemi `Program` `MyApplication.Core` ad alanındaki sınıfının içindeyse, derleyici seçeneğinin olması gerekir `-main:MyApplication.Core.Program` .

## <a name="remarks"></a>Açıklamalar

Derlemeniz bir [ana](../../programming-guide/main-and-command-args/index.md) yöntemle birden fazla tür içeriyorsa, programa giriş noktası olarak kullanmak istediğiniz **ana** yöntemi içeren türü belirtebilirsiniz.

Bu seçenek bir *. exe* dosyası derlenirken kullanım içindir.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikler** sayfasını açın.

2. **Uygulama** Özellik sayfasına tıklayın.

3. **Başlangıç nesnesi** özelliğini değiştirin.

    Bu derleyici seçeneğini program aracılığıyla ayarlamak için, bkz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A> ..

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a>Bu derleyici seçeneğini *. csproj* dosyasını el ile düzenleyerek ayarlamak için

Bu seçeneği,. csproj dosyasını düzenleyerek ve bölümünün içine bir öğe ekleyerek ayarlayabilirsiniz `StartupObject` `PropertyGroup` . Örneğin:

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a>Örnek

`t2.cs`Ve `t3.cs` ' de **Main** yönteminin bulunduğunu belirterek derleyin `Test2` :

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
