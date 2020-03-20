---
title: 'Nasıl yapilir: Derlemeyi genel derleme önbelleğine yükleme'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155569"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Nasıl yapilir: Derlemeyi genel derleme önbelleğine yükleme

Genel derleme önbelleği (GAC), çeşitli uygulamaların paylaştığı derlemeleri depolar. Aşağıdaki bileşenlerden biriyle bir derlemeyi [genel montaj önbelleğine](gac.md) yükleyin:

- [Windows Installer](#windows-installer)
- [Genel Montaj Önbellek aracı](#global-assembly-cache-tool)

> [!IMPORTANT]
> Genel derleme önbelleğine yalnızca güçlü adlandırılmış derlemeler yükleyebilirsiniz. Güçlü adlandırılmış bir derlemenin nasıl oluşturulabildiğini öğrenmek için [bkz.](../../standard/assembly/sign-strong-name.md)

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), Windows yükleme motoru, genel derleme önbelleğine derlemeler eklemek için önerilen yoldur. Windows Installer, genel derleme önbelleğindeki derlemelerin başvuru sayımını ve diğer avantajları sağlar. Windows Installer için yükleyici paketi oluşturmak [için Visual Studio 2017 için WiX araç seti uzantısını](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanın.

## <a name="global-assembly-cache-tool"></a>Genel Montaj Önbellek aracı

[.NET Global Assembly Cache yardımcı programını (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) genel derleme önbelleğine derlemeler eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için kullanabilirsiniz.

   > [!NOTE]
   > *Gacutil.exe* sadece geliştirme amaçlıdır. Üretim derlemelerini genel derleme önbelleğine yüklemek için kullanmayın.

GAC bir derleme yüklemek için *gacutil.exe* kullanmak için sözdizimi aşağıdaki gibidir:

```cmd
gacutil -i <assembly name>
```

Bu komutta, * \<derleme adı>,* genel derleme önbelleğine yüklenmesi gereken derlemenin adıdır.

*gacutil.exe* sistem yolunuzda değilse, [VS * \<sürümü>* için Geliştirici komut istemini ](../tools/developer-command-prompt-for-vs.md)kullanın.

Aşağıdaki örnek, genel derleme önbelleğine dosya adı *hello.dll* içeren bir derleme yükler.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> .NET Framework'ün önceki sürümlerinde, *Shfusion.dll* Windows kabuk uzantısı derlemeleri Dosya Gezgini'ne sürükleyerek yüklemenize olanak sağlar. .NET Framework 4 ile başlayarak, *Shfusion.dll* eskidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler ve genel montaj önbelleği yle çalışma](working-with-assemblies-and-the-gac.md)
- [Nasıl yapilir: Derlemeyi genel montaj önbelleğinden kaldırma](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (Küresel Montaj Önbellek aracı)](../tools/gacutil-exe-gac-tool.md)
- [Nasıl yapilir: Güçlü bir ada sahip bir derlemeyi imzalama](../../standard/assembly/sign-strong-name.md)
