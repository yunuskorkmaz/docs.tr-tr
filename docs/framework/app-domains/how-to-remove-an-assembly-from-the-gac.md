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
ms.openlocfilehash: 6c5f47f4c33f725377281146bef0a37dbd3f774c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753735"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Nasıl yapılır: Bir Derlemeyi Genel Derleme Önbelleğinden Kaldırma
Bir derlemeyi genel derleme önbelleğinden (GAC) kaldırmak için iki yolu vardır:  
  
-   Kullanarak [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Geliştirme ve sınama sırasında GAC'ye yerleştirdiğiniz derlemeleri kaldırmak için bu seçeneği kullanın.  
  
-   Kullanarak [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx). Derlemeleri yükleme paketleri sınarken ve üretim sistemleri için kaldırmak için bu seçeneği kullanmanız gerekir.  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>Gacutil.exe ile bir derlemeyi kaldırma  
  
1.  Komut satırında, aşağıdaki komutu yazın:  
  
     **Gacutil – u** \< *derleme adı*>  
  
     Bu komutta *derleme adı* genel derleme önbelleğinden kaldırılacak derleme adıdır.  
  
    > [!WARNING]
    >  Gacutil.exe, üretim sistemleri derlemelerini derleme hala bazı uygulama tarafından gerekebilir olasılığı nedeniyle kaldırmak için kullanmamalısınız. Bunun yerine, her derlemeyi GAC'ye yükler için bir başvuru sayımı tutar Windows Installer kullanmanız gerekir.  
  
 Aşağıdaki örnek adlı bir derleme kaldırır `hello.dll` genel derleme önbelleğinden.  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>Windows Installer ile bir derlemeyi kaldırma  
  
1.  Gelen **programlar ve Özellikler** uygulamada **Denetim Masası**, kaldırmak istediğiniz uygulamayı seçin. Yükleme paketi GAC'ye derlemeleri yerleştirdiyseniz, başka bir uygulama tarafından kullanılmaz, Windows Installer bunları kaldırır.  
  
    > [!NOTE]
    >  Windows Installer GAC'de kurulu derlemeler için bir başvuru sayımı tutar. Yalnızca kendi başvuru sayısı, Windows Installer paketiyle yüklenen herhangi bir uygulama tarafından kullanılıp kullanılmadığını gösteren sıfır ulaştığında bir derlemeyi GAC kaldırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğine Yükleme](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
