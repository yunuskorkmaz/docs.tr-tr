---
title: 'Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler'
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
ms.openlocfilehash: 8e2d051cda9861da1af2caa65160b6e753b24bd1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926508"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler

Genel bütünleştirilmiş kod önbelleği (GAC), birkaç uygulamanın paylaştığı derlemeleri depolar. Aşağıdaki bileşenlerden biriyle bir derlemeyi [genel bütünleştirilmiş kod önbelleğine](gac.md) yükler: 

- [Windows Installer](#windows-installer)
- [Genel derleme önbelleği aracı](#global-assembly-cache-tool)

> [!IMPORTANT]
> GAC 'ye yalnızca tanımlayıcı adlı derlemeler yükleyebilirsiniz. Tanımlayıcı adlı bütünleştirilmiş kod oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir derlemeyi güçlü bir adla](how-to-sign-an-assembly-with-a-strong-name.md)imzalayın.

## <a name="windows-installer"></a>Windows Installer

Windows yükleme altyapısı [Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), genel derleme önbelleğine derlemeler eklemenin önerilen yoludur. Windows Installer, genel derleme önbelleğindeki derlemelerin ve diğer avantajlardan başvuru saymasını sağlar. Windows Installer için bir yükleyici paketi oluşturmak için, [Visual Studio 2017 Için Wix araç takımı uzantısını](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanın.

## <a name="global-assembly-cache-tool"></a>Genel derleme önbelleği aracı

Genel bütünleştirilmiş kod önbelleğine derleme eklemek ve genel derleme önbelleğinin içeriğini görüntülemek için [genel derleme önbelleği aracını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) kullanabilirsiniz.

   > [!NOTE]
   > *Gacutil. exe* yalnızca geliştirme amaçlıdır. Bu uygulamayı, genel derleme önbelleğine üretim derlemeleri yüklemek için kullanmayın.

GAC 'de bir derlemeyi yüklemek için *Gacutil. exe* ' yi kullanma söz dizimi aşağıdaki gibidir:

```console
gacutil -i <assembly name>
```

Bu komutta,  *\<derleme adı >* , genel derleme önbelleğine yüklenecek derlemenin adıdır.

*Gacutil. exe* dosyası sistem yolunuzda değilse, [vs  *\<sürüm >* için geliştirici komut istemi](../tools/developer-command-prompt-for-vs.md)kullanın.

Aşağıdaki örnek, *Hello. dll* dosya adına sahip bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler.

```console
gacutil -i hello.dll
```

> [!NOTE]
> .NET Framework önceki sürümlerinde, *Shfusion. dll* Windows kabuğu uzantısı, derlemeleri dosya Gezgini 'ne sürükleyerek yüklemenizi sağlar. .NET Framework 4 ' ten başlayarak *Shfusion. dll* artık kullanılmıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler ve genel derleme önbelleği ile çalışma](working-with-assemblies-and-the-gac.md)
- [Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırma](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil. exe (genel derleme önbelleği aracı)](../tools/gacutil-exe-gac-tool.md)
- [Nasıl yapılır: Bir derlemeyi güçlü bir adla imzala](how-to-sign-an-assembly-with-a-strong-name.md)
