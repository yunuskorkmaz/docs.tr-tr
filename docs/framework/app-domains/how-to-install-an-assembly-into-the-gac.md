---
title: Bir derlemeyi GAC içine yükleme
ms.date: 09/20/2018
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584587"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme

Bir katı adlı derlemeyi genel bütünleştirilmiş kod önbelleğine (GAC) yüklemenin iki yolu vardır.

> [!IMPORTANT]
> Yalnızca katı adlı derlemeler GAC içine yüklenebilir. Bir katı adlı derleme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), Windows yükleme altyapısı, derlemeleri genel bütünleştirilmiş kod önbelleğine eklemek için önerilen yoludur. Windows Installer, derlemeleri genel derleme önbelleğini ve diğer avantajlar başvuru sayımı sağlar. Kullanabileceğiniz [WiX Toolset uzantı Visual Studio 2017 için](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) Windows Yükleyicisi için bir yükleyici paketi oluşturmak için.

## <a name="global-assembly-cache-tool"></a>Genel Derleme Önbelleği Aracı

Kullanabileceğiniz [Genel Derleme Önbelleği aracını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) genel derleme önbelleğine katı adlı derlemeler eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için.

   > [!NOTE]
   > Gacutil.exe yalnızca geliştirme amaçlıdır ve genel bütünleştirilmiş kod önbelleğine üretim derlemeleri yüklemek için kullanılmamalıdır.

Gacutil sözdizimi aşağıdaki gibidir:

```shell
gacutil -i <assembly name>
```

Bu komutta *derleme adı* genel bütünleştirilmiş kod önbelleğine yüklenecek derlemenin adıdır.

Aşağıdaki örnek, dosya adı ile bir derlemeyi yükler `hello.dll` genel bütünleştirilmiş kod önbelleğine.

```shell
gacutil -i hello.dll
```

> [!NOTE]
> Önceki .NET Framework sürümlerinde, Shfusion.dll Windows kabuk uzantısı, bunları sürükleyerek derlemeleri yüklemek etkin **dosya Gezgini**. .NET Framework 4 ile başlayarak, Shfusion.dll kullanımdan kalkmıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](working-with-assemblies-and-the-gac.md)
- [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğinden Kaldırma](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
- [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](how-to-sign-an-assembly-with-a-strong-name.md)