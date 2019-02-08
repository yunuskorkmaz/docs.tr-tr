---
title: 'Nasıl yapılır: Bir derlemeyi genel derleme önbelleğine yükleme'
ms.date: 02/05/2019
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
ms.openlocfilehash: adeaaa6626a1c9e9e4543613a8fa9e94d2b67e89
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826843"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Nasıl yapılır: Bir derlemeyi genel derleme önbelleğine yükleme

Bazı uygulamalar paylaşan derlemeleri genel bütünleştirilmiş kod önbelleği (GAC) depolar. Bütünleştirilmiş kod içine yüklemek [genel derleme önbelleği](https://docs.microsoft.com/en-us/dotnet/framework/app-domains/gac) aşağıdaki bileşenlerden biri ile: 
- [Windows Installer](#windows-installer)
- [Genel Derleme Önbelleği Aracı](#global-assembly-cache-tool)

> [!IMPORTANT]
> Yalnızca katı adlı derlemeler GAC içine yükleyebilirsiniz. Bir katı adlı derleme oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir derlemeyi katı bir adla imzalamak](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](https://docs.microsoft.com/en-us/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), Windows yükleme altyapısı, derlemeleri genel bütünleştirilmiş kod önbelleğine eklemek için önerilen yoludur. Windows Installer, derlemeleri genel derleme önbelleğini ve diğer avantajlar başvuru sayımı sağlar. İçin Windows Installer bir yükleyici paketi oluşturmak için kullanın [WiX toolset uzantı Visual Studio 2017 için](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Genel Derleme Önbelleği Aracı

Kullanabileceğiniz [Genel Derleme Önbelleği aracını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) derlemeleri genel derleme önbelleğine ekleme ve genel derleme önbelleğinin içeriğini görüntülemek için.

   > [!NOTE]
   > *Gacutil.exe* yalnızca geliştirme amaçlıdır. Genel bütünleştirilmiş kod önbelleğine üretim derlemeleri yüklemek için kullanmayın.

Kullanmaya ilişkin sözdizimini *gacutil.exe* bir derlemeyi GAC'ye yüklemek için şu şekilde olur:

```console
gacutil -i <assembly name>
```

Bu komutta  *\<derleme adı >* genel bütünleştirilmiş kod önbelleğine yüklenecek derlemenin adıdır.

Varsa *gacutil.exe* kullanın, sistem yolunda değil [VS için geliştirici komut istemi  *\<sürüm >*](https://docs.microsoft.com/en-us/dotnet/framework/tools/developer-command-prompt-for-vs).

Aşağıdaki örnek, dosya adı ile bir derlemeyi yükler *hello.dll* genel bütünleştirilmiş kod önbelleğine.

```console
gacutil -i hello.dll
```

> [!NOTE]
> .NET Framework'ün önceki sürümlerindeki *Shfusion.dll* Windows kabuk uzantısı derlemeleri dosya Gezgini'nde sürükleyerek yüklemenize olanak tanır. .NET Framework 4 ile başlayarak *Shfusion.dll* kullanımdan kalkmıştır.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler ve genel derleme önbelleği ile çalışma](working-with-assemblies-and-the-gac.md)
- [Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırma](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
- [Nasıl yapılır: Derlemeyi tanımlayıcı bir adla imzalama](how-to-sign-an-assembly-with-a-strong-name.md)