---
title: Microsoft. NET. SDK. Desktop için MSBuild özellikleri
description: WPF ve WinForms içeren, .NET masaüstü SDK 'Sı tarafından anlayan olan MSBuild özellikleri ve öğeleri için başvuru.
ms.date: 02/04/2021
ms.topic: reference
author: adegeo
ms.author: adegeo
ms.custom: updateeachrelease
no-loc:
- App.xaml
- Application.xaml
- ApplicationDefinition
- Page
- EmbeddedResource
- Compile
- None
ms.openlocfilehash: 6d1903558dd03776a72eb6ee56ddae09fb66615b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488368"
---
# <a name="msbuild-reference-for-net-desktop-sdk-projects"></a>.NET masaüstü SDK projeleri için MSBuild başvurusu

Bu sayfa, .NET masaüstü SDK ile Windows Forms (WinForms) ve Windows Presentation Foundation (WPF) projelerini yapılandırmak için kullandığınız MSBuild özelliklerine ve öğelerine yönelik bir başvurudur.

> [!NOTE]
> Bu makale, masaüstü uygulamalarıyla ilişkili olarak .NET SDK için MSBuild özelliklerinin bir alt kümesini belgeler. Ortak .NET SDK 'ya özgü MSBuild özelliklerinin bir listesi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](msbuild-props.md). Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="enable-net-desktop-sdk"></a>.NET masaüstü SDK 'sını etkinleştir

WinForms veya WPF kullanmak için, proje dosyanızı yapılandırın.

### <a name="net-50"></a>.NET 5.0

WinForms veya WPF projenizin proje dosyasında aşağıdaki ayarları belirtin:

- .NET SDK 'sını hedefleyin `Microsoft.NET.Sdk` . Daha fazla bilgi için bkz. [proje dosyaları](overview.md#project-files).
- [`TargetFramework`](msbuild-props.md#targetframework)Olarak ayarlayın `net5.0-windows` .
- UI çerçevesi özelliği ekleyin (veya gerekirse her ikisi de):
  - [`UseWPF`](#usewpf)WPF 'yi `true` içeri ve daha sonra kullanmak için olarak ayarlayın.
  - [`UseWindowsForms`](#usewindowsforms) `true` WinForms içeri aktarıp kullanmak için olarak ayarlayın.
- Seçim `OutputType` Olarak ayarlayın `WinExe` . Bu, bir kitaplık yerine bir uygulama oluşturur. Bir kitaplık oluşturmak için bu özelliği atlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

### <a name="net-core-31"></a>.NET Core 3.1

WinForms veya WPF projenizin proje dosyasında aşağıdaki ayarları belirtin:

- .NET SDK 'sını hedefleyin `Microsoft.NET.Sdk.WindowsDesktop` . Daha fazla bilgi için bkz. [proje dosyaları](overview.md#project-files).
- [`TargetFramework`](msbuild-props.md#targetframework)Olarak ayarlayın `netcoreapp3.1` .
- UI çerçevesi özelliği ekleyin (veya gerekirse her ikisi de):
  - [`UseWPF`](#usewpf)WPF 'yi `true` içeri ve daha sonra kullanmak için olarak ayarlayın.
  - [`UseWindowsForms`](#usewindowsforms) `true` WinForms içeri aktarıp kullanmak için olarak ayarlayın.
- Seçim `OutputType` Olarak ayarlayın `WinExe` . Bu, bir kitaplık yerine bir uygulama oluşturur. Bir kitaplık oluşturmak için bu özelliği atlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>

    <UseWPF>true</UseWPF>
    <!-- and/or -->
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

## <a name="wpf-default-includes-and-excludes"></a>WPF varsayılan içerir ve dışlar

SDK projeleri, dosyaları projeden örtük olarak dahil etmek veya hariç tutmak için bir kurallar kümesi tanımlar. Bu kurallar, dosyanın derleme eylemini de otomatik olarak ayarlar. Bu, varsayılan içerme veya dışlama kuralları olmayan, daha eski SDK olmayan .NET Framework projelerinin aksine. .NET Framework projeler, projeye hangi dosyaların ekleneceğini açıkça bildirmeniz gerekir.

.NET proje dosyaları, dosyaları otomatik olarak işlemeye yönelik [Standart bir kurallar kümesi](overview.md#default-includes-and-excludes) içerir. WPF projeleri ek kurallar ekler.

Aşağıdaki tabloda, [](https://en.wikipedia.org/wiki/Glob_(programming)) [`UseWPF`](#usewpf) Proje özelliği olarak ayarlandığında .net masaüstü SDK 'sına dahil edilen ve çıkarılan öğelerin ve genelleştirmeler gösterilmektedir `true` :

| Öğe               | Glob 'yi dahil et                 | Glob 'yi hariç tut                                                                                           | Glob 'yi kaldır  |
|-----------------------|------------------------------|--------------------------------------------------------------------|--------------|
| ApplicationDefinition | App.xaml veya Application.xaml | Yok                                                                | Yok          |
| Page                  | \*\*/\*. xaml                 | \*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc<br>Tarafından tanımlanan XAML *ApplicationDefinition* | Yok          |
| None                  | Yok                          | Yok                                                                | \*\*/\*. xaml |

Tüm proje türleri için varsayılan içerme ve dışlama ayarları aşağıda verilmiştir. Daha fazla bilgi için bkz. [varsayılan içerme ve dışladığı](overview.md#default-includes-and-excludes).

| Öğe           | Glob 'yi dahil et                              | Glob 'yi hariç tut                                                  | Glob 'yi kaldır              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compile           | \*\*/\*.cs \*\*/\*. vb (veya diğer dil uzantıları) | \*\*/\*kullanıcısını  \*\*/\*.\* PROJ  \*\*/\*. sln  \*\*/\*. vssscc  | Yok          |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc     | Yok                      |
| None              | \*\*/\*                                   | \*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc     | \*\*/\*.cs \*\*/\*. resx |

### <a name="errors-related-to-duplicate-items"></a>"Yinelenen" öğelerle ilgili hatalar

Projenize açıkça dosya eklediyseniz ya da XAML genelleştirmeler otomatik olarak dosya eklemek istiyorsanız, aşağıdaki hatalardan birini alabilirsiniz:

* Yinelenen ' ApplicationDefinition ' öğeleri eklendi.
* Yinelenen ' Page ' öğeleri eklendi.

Bu hatalar, ayarlarınızdaki örtük *ekleme* genelleştirmeler çelişen bir sonucudur. Bu sorunu geçici olarak çözmek için ya da [`EnableDefaultApplicationDefinition`](#enabledefaultapplicationdefinition) [`EnableDefaultPageItems`](#enabledefaultpageitems) olarak ayarlayın `false` . Bu değerleri `false` , projenizde varsayılan genelleştirmeler açıkça tanımlamanız gereken önceki SDK 'ların davranışına geri dönmek veya projeye dahil edilecek dosyaları açıkça tanımlamanız için ayarlamak.

[ `EnableDefaultItems` Özelliğini](msbuild-props.md#enabledefaultitems) olarak ayarlayarak tüm örtük eklemeleri tamamen devre dışı bırakabilirsiniz `false` .

## <a name="wpf-settings"></a>WPF ayarları

- [UseWPF](#usewpf)
- [EnableDefaultApplicationDefinition](#enabledefaultapplicationdefinition)
- [EnableDefault Page öğeleri](#enabledefaultpageitems)

WPF 'e özgü olmayan proje ayarları hakkında daha fazla bilgi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](msbuild-props.md).

### <a name="usewpf"></a>UseWPF

`UseWPF`ÖZELLIĞI WPF kitaplıklarına başvuruların eklenip eklenmeyeceğini denetler. Bu Ayrıca, bir WPF projesini ve ilgili dosyaları doğru şekilde işlemek için MSBuild ardışık düzenini değiştirir. `false` varsayılan değerdir. `UseWPF` `true` WPF desteğini etkinleştirmek için özelliğini olarak ayarlayın. Yalnızca bu özellik etkinleştirildiğinde Windows platformunu hedefleyebilirsiniz.

```xml
<PropertyGroup>
  <UseWPF>true</UseWPF>
</PropertyGroup>
```

Bu özellik olarak ayarlandığında `true` , .NET 5.0 + projeleri, [.net masaüstü SDK 'sını](#enable-net-desktop-sdk)otomatik olarak içeri aktarır.

.NET Core 3,1 projelerinin, bu özelliği kullanmak için [.net masaüstü SDK 'sını](#enable-net-desktop-sdk) açık bir şekilde hedeflemesi gerekir.

### <a name="enabledefaultapplicationdefinition"></a>EnableDefaultApplicationDefinition

`EnableDefaultApplicationDefinition`Özelliği, `ApplicationDefinition` öğelerin projeye örtük olarak dahil edilip edilmediğini denetler. `true` varsayılan değerdir. `EnableDefaultApplicationDefinition` `false` Örtük dosya eklemeyi devre dışı bırakmak için özelliğini olarak ayarlayın.

```xml
<PropertyGroup>
  <EnableDefaultApplicationDefinition>false</EnableDefaultApplicationDefinition>
</PropertyGroup>
```

Bu özellik, varsayılan ayar olan [ `EnableDefaultItems` özelliği](msbuild-props.md#enabledefaultitems) özelliğinin olarak ayarlanmasını gerektirir `true` .

### <a name="enabledefaultpageitems"></a>EnableDefault Page öğeleri

`EnableDefaultPageItems`Özelliği, `Page` _. xaml_ dosyaları olan öğelerin projeye örtük olarak dahil edilip edilmeyeceğini denetler. `true` varsayılan değerdir. `EnableDefaultPageItems` `false` Örtük dosya eklemeyi devre dışı bırakmak için özelliğini olarak ayarlayın.

```xml
<PropertyGroup>
  <EnableDefaultPageItems>false</EnableDefaultPageItems>
</PropertyGroup>
```

Bu özellik, varsayılan ayar olan [ `EnableDefaultItems` özelliği](msbuild-props.md#enabledefaultitems) özelliğinin olarak ayarlanmasını gerektirir `true` .

## <a name="windows-forms-settings"></a>Windows Forms ayarları

- [UseWindowsForms](#usewindowsforms)

WinForms 'e özgü olmayan proje özellikleri hakkında daha fazla bilgi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](msbuild-props.md).

### <a name="usewindowsforms"></a>UseWindowsForms

`UseWindowsForms`Özelliği, uygulamanızın Windows Forms hedefte oluşturulup oluşturulmayacağını denetler. Bu özellik, bir Windows Forms projesini ve ilgili dosyaları doğru şekilde işlemek için MSBuild ardışık düzenini değiştirir. `false` varsayılan değerdir. `UseWindowsForms` `true` Windows Forms desteğini etkinleştirmek için özelliğini olarak ayarlayın. Bu ayar etkinleştirildiğinde yalnızca Windows platformunu hedefleyebilirsiniz.

```xml
<PropertyGroup>
  <UseWindowsForms>true</UseWindowsForms>
</PropertyGroup>
```

Bu özellik olarak ayarlandığında `true` , .NET 5.0 + projeleri, [.net masaüstü SDK 'sını](#enable-net-desktop-sdk)otomatik olarak içeri aktarır.

.NET Core 3,1 projelerinin, bu özelliği kullanmak için [.net masaüstü SDK 'sını](#enable-net-desktop-sdk) açık bir şekilde hedeflemesi gerekir.

## <a name="shared-settings"></a>Paylaşılan ayarlar

- [Disablewinexeoutputçıkarımı](#disablewinexeoutputinference)

### <a name="disablewinexeoutputinference"></a>Disablewinexeoutputçıkarımı

.NET 5,0 SDK ve üzeri için geçerlidir.

Bir uygulama `Exe` özelliği için ayarlanan değere sahip olduğunda `OutputType` , uygulama bir konsoldan çalışmıyorsa bir konsol penceresi oluşturulur. Bu, genellikle bir Windows masaüstü uygulamasının istenen davranışından değildir. Değeri ile `WinExe` bir konsol penceresi oluşturulmaz. .NET 5,0 SDK ile başlayarak, `Exe` değer otomatik olarak olarak dönüştürülür `WinExe` .

`DisableWinExeOutputInference`Özelliği olarak davranma davranışını geri döndürür `Exe` `WinExe` . `true`Özellik değerinin davranışını geri yüklemek için bu değeri olarak ayarlayın `OutputType` `Exe` . `false` varsayılan değerdir.

```xml
<PropertyGroup>
  <DisableWinExeOutputInference>true</DisableWinExeOutputInference>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET projesi SDK 'Ları](overview.md)
- [.NET SDK projeleri için MSBuild başvurusu](msbuild-props.md)
- [MSBuild şema başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)
- [Bir derlemeyi özelleştirme](/visualstudio/msbuild/customize-your-build)
