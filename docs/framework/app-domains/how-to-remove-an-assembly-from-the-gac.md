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
ms.openlocfilehash: b9bece9e21a29e10f08d53c5e98f01cf02602e18
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231029"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma
Bir derlemeyi genel derleme önbelleğinden (GAC) kaldırmak için iki yolu vardır:  
  
-   Kullanarak [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Geliştirme ve test sırasında GAC'de koyduğunuz derlemeleri kaldırmak üzere bu seçeneği kullanabilirsiniz.  
  
-   Kullanarak [Windows Installer](/windows/desktop/Msi/windows-installer-portal). Yükleme paketleri sınarken ve üretim sistemler için derlemeleri kaldırmak için bu seçeneği kullanmanız gerekir.  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>Bir derlemeyi Gacutil.exe ile kaldırma  
  
1.  Komut satırında, aşağıdaki komutu yazın:  
  
     **Gacutil – u** \< *derleme adı*>  
  
     Bu komutta *derleme adı* derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırmak için adıdır.  
  
    > [!WARNING]
    >  Gacutil.exe derleme yine de bazı uygulama tarafından gerekebilir olasılığı nedeniyle üretim sistemlerine derlemeleri kaldırmak için kullanmamanız gerekir. Bunun yerine, her derlemeyi GAC'ye yükler için bir başvuru sayısını tutar Windows Installer kullanmanız gerekir.  
  
 Aşağıdaki örnekte adlı bir derleme kaldırır `hello.dll` genel bütünleştirilmiş kod önbelleğinden.  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>Bir derlemeyi Windows Installer ile kaldırma  
  
1.  Gelen **programlar ve Özellikler** uygulamada **Denetim Masası**, kaldırmak istediğiniz uygulamayı seçin. Yükleme paketini derlemeleri GAC'ye yerleştirdiyseniz başka bir uygulama tarafından kullanılmaz, Windows Installer bunları kaldırır.  
  
    > [!NOTE]
    >  Windows Installer GAC'de kurulu derlemeler için bir başvuru sayısını tutar. Yalnızca, başvuru sayısı, Windows Installer paketi ile yüklü herhangi bir uygulama tarafından kullanılıp kullanılmadığını gösteren sıfır ulaştığında bir derlemenin GAC kaldırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğine Yükleme](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
