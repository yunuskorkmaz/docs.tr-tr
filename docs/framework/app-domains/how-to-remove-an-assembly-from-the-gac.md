---
title: 'Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa88cbc73415695a1545704a2ad8cab535f011e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053138"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma

Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden (GAC) kaldırmanın iki yolu vardır:

- [Genel derleme önbelleği aracını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md)kullanarak. Geliştirme ve test sırasında GAC 'ye yerleştirdiğiniz derlemeleri kaldırmak için bu seçeneği kullanabilirsiniz.

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)kullanarak. Yükleme paketlerini ve üretim sistemlerini test ederken derlemeleri kaldırmak için bu seçeneği kullanmanız gerekir.

### <a name="removing-an-assembly-with-gacutilexe"></a>Gacutil. exe ile bir derlemeyi kaldırma

1. Komut satırında, aşağıdaki komutu yazın:

    **Gacutil – u** *bütünleştirilmiş kod adı* \<>

    Bu komutta, *derleme adı* genel derleme önbelleğinden kaldırılacak derlemenin adıdır.

    > [!WARNING]
    > Derlemenin bazı uygulamalar için hala gerekli olabileceği için, üretim sistemlerindeki derlemeleri kaldırmak üzere Gacutil. exe ' yi kullanmamalısınız. Bunun yerine, GAC içinde yüklediği her derleme için başvuru sayısını tutan Windows Installer kullanmanız gerekir.

 Aşağıdaki örnek, genel derleme önbelleğinden adlı `hello.dll` bir derlemeyi kaldırır.

```
gacutil -u hello
```

### <a name="removing-an-assembly-with-windows-installer"></a>Windows Installer bir derlemeyi kaldırma

1. **Denetim Masası**'ndaki **Programlar ve Özellikler** uygulamasında kaldırmak istediğiniz uygulamayı seçin. Yükleme paketi GAC 'ye derlemeler yerleştirirse, Windows Installer başka bir uygulama tarafından kullanılmıyorsa, bu dosyaları kaldırır.

    > [!NOTE]
    > Windows Installer GAC 'de yüklü derlemeler için bir başvuru sayısı tutar. Bir derleme GAC 'den yalnızca başvuru sayısı sıfıra ulaştığında kaldırılır. Bu, bir Windows Installer paketi tarafından yüklenen herhangi bir uygulama tarafından kullanılmadığını gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](working-with-assemblies-and-the-gac.md)
- [Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler](install-assembly-into-gac.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
