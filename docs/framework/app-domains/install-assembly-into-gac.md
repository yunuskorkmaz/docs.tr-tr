---
title: 'Nasıl yapılır: Bir bütünleştirilmiş kodu genel derleme önbelleğine yükleme'
description: Bir derlemeyi, .NET 'teki genel derleme önbelleği 'ne (GAC) yükleyerek birçok uygulama tarafından paylaşılabilir. Windows Installer veya GAC yardımcı programını kullanın.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104660"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Nasıl yapılır: Bir bütünleştirilmiş kodu genel derleme önbelleğine yükleme

Genel bütünleştirilmiş kod önbelleği (GAC), birkaç uygulamanın paylaştığı derlemeleri depolar. Aşağıdaki bileşenlerden biriyle bir derlemeyi [genel bütünleştirilmiş kod önbelleğine](gac.md) yükler:

- [Windows Installer](#windows-installer)
- [Genel derleme önbelleği aracı](#global-assembly-cache-tool)

> [!IMPORTANT]
> Genel bütünleştirilmiş kod önbelleğine yalnızca tanımlayıcı adlı derlemeler yükleyebilirsiniz. Tanımlayıcı adlı bütünleştirilmiş kod oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

Windows yükleme altyapısı [Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), genel derleme önbelleğine derlemeler eklemenin önerilen yoludur. Windows Installer, genel derleme önbelleğindeki derlemelerin ve diğer avantajlardan başvuru saymasını sağlar. Windows Installer için bir yükleyici paketi oluşturmak için, [Visual Studio 2017 Için Wix araç takımı uzantısını](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanın.

## <a name="global-assembly-cache-tool"></a>Genel derleme önbelleği aracı

Genel derleme önbelleğine derleme eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için [.NET genel derleme önbelleği yardımcı programını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) kullanabilirsiniz.

   > [!NOTE]
   > *Gacutil.exe* yalnızca geliştirme amaçlıdır. Bu uygulamayı, genel derleme önbelleğine üretim derlemeleri yüklemek için kullanmayın.

GAC 'de bir derlemeyi yüklemek için *gacutil.exe* kullanmak için sözdizimi aşağıdaki gibidir:

```cmd
gacutil -i <assembly name>
```

Bu komutta, *\<assembly name>* genel derleme önbelleğine yüklenecek derlemenin adıdır.

*gacutil.exe* sistem yolunuzda yoksa, [vs *\<version>* için geliştirici komut istemi ](../tools/developer-command-prompt-for-vs.md)' ni kullanın.

Aşağıdaki örnek, *hello.dll* dosya adı olan bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklenir.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> .NET Framework önceki sürümlerinde, *Shfusion.dll* Windows kabuğu uzantısı, derlemeleri dosya Gezgini 'ne sürükleyerek yüklemenizi sağlar. .NET Framework 4 ' ten başlayarak *Shfusion.dll* artık kullanılmıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler ve genel derleme önbelleği ile çalışma](working-with-assemblies-and-the-gac.md)
- [Nasıl yapılır: genel bütünleştirilmiş kod önbelleğinden bir derlemeyi kaldırma](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (genel derleme önbelleği aracı)](../tools/gacutil-exe-gac-tool.md)
- [Nasıl yapılır: bir derlemeyi güçlü bir adla Imzalama](../../standard/assembly/sign-strong-name.md)
