---
title: 'Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma'
description: Genel derleme önbelleği aracını (Gacutil.exe) veya Windows Installer kullanarak .NET 'teki genel derleme önbelleğinden bir derlemeyi kaldırmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
ms.openlocfilehash: e3a596ea6029ded190c33032e96b601de9d4012d
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104769"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma

Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden (GAC) kaldırmanın iki yolu vardır:

- [Genel derleme önbelleği aracını (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md)kullanarak. Geliştirme ve test sırasında GAC 'ye yerleştirdiğiniz derlemeleri kaldırmak için bu seçeneği kullanabilirsiniz.

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)kullanarak. Yükleme paketlerini ve üretim sistemlerini test ederken derlemeleri kaldırmak için bu seçeneği kullanmanız gerekir.

## <a name="removing-an-assembly-with-gacutilexe"></a>Gacutil.exe bir derlemeyi kaldırma

Komut isteminde aşağıdaki komutu yazın:

**Gacutil – u**\<*assembly name*>

Bu komutta, *derleme adı* genel derleme önbelleğinden kaldırılacak derlemenin adıdır.

> [!WARNING]
> Derlemenin bazı uygulamalar tarafından hala gerekli olabileceğinden, üretim sistemlerindeki derlemeleri kaldırmak için Gacutil.exe kullanmamalısınız. Bunun yerine, GAC içinde yüklediği her derleme için başvuru sayısını tutan Windows Installer kullanmanız gerekir.

Aşağıdaki örnek, genel derleme önbelleğinden adlı bir derlemeyi kaldırır `hello.dll` :

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a>Windows Installer bir derlemeyi kaldırma

**Denetim Masası**'ndaki **Programlar ve Özellikler** uygulamasında kaldırmak istediğiniz uygulamayı seçin. Yükleme paketi GAC 'ye derlemeler yerleştirirse, Windows Installer başka bir uygulama tarafından kullanılmıyorsa, bu dosyaları kaldırır.

> [!NOTE]
> Windows Installer GAC 'de yüklü derlemeler için bir başvuru sayısı tutar. Bir derleme GAC 'den yalnızca başvuru sayısı sıfıra ulaştığında kaldırılır. Bu, bir Windows Installer paketi tarafından yüklenen herhangi bir uygulama tarafından kullanılmadığını gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler ve Genel Derleme Önbelleği ile Çalışma](working-with-assemblies-and-the-gac.md)
- [Nasıl yapılır: bir derlemeyi genel derleme önbelleğine yüklemek](install-assembly-into-gac.md)
- [Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
