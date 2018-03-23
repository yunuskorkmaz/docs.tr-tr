---
title: -platform (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09c7d677e614186d26a2ff8a1ce2fe5213cf7799
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-platform-visual-basic"></a>-platform (Visual Basic)
Ortak dil çalışma zamanı (CLR) hangi platformu sürümü çıktı dosyasını çalıştırıp belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`x86`|32-bit, x86 uyumlu CLR tarafından çalıştırılacak derlemenizi birleştirir.|  
|`x64`|AMD64 veya EM64T yönerge kümesi destekleyen bir bilgisayarda 64-bit CLR tarafından çalıştırılacak derlemenizi birleştirir.|  
|`Itanium`|64-bit CLR tarafından Itanium işlemcili bir bilgisayarda çalıştırılması için derlemenizi birleştirir.|  
|`arm`|ARM (Gelişmiş RISC makinesi) işlemciye sahip bir bilgisayarda çalıştırılacak derlemenizi birleştirir.|  
|`anycpu`|Herhangi bir platformda çalıştırılacak derlemenizi birleştirir. Uygulama 32 bit uygulama 32 bit Windows sürümleri üzerinde ve Windows 64 bit sürümlerinde 64-bit uygulama olarak çalışır. Bu bayrak varsayılan değerdir.|  
|`anycpu32bitpreferred`|Herhangi bir platformda çalıştırılacak derlemenizi birleştirir. Uygulama 32 bit uygulama olarak, Windows'un 32 bit ve 64 bit sürümlerinde çalışır. Bu bayrak, yalnızca yürütülebilir dosyalar için geçerlidir (. EXE) ve gerektirir [!INCLUDE[net_v45](~/includes/net-v45-md.md)].|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `-platform` seçeneği çıktı dosyası tarafından hedeflenen işlemci türünü belirtin.  
  
 Genel olarak, Visual Basic'te yazılmış .NET Framework derlemeleri aynı platformdan bağımsız olarak çalışır. Ancak, farklı platformlarda farklı şekilde davranan bazı durumlar vardır. Bu ortak çalışmalarını şunlardır:  
  
-   Herhangi bir işaretçi türü gibi platforma bağlı olarak boyutunu değiştirme üyeleri içeren yapıları.  
  
-   Sabit boyutlar içeren işaretçi aritmetiği.  
  
-   Tanıtıcılar için `Integer` yerine <xref:System.IntPtr> kullanan yanlış platform çağrıları veya COM bildirimleri.  
  
-   Atama <xref:System.IntPtr> için `Integer`.  
  
-   Platform kullanarak çağırma veya COM birlikte çalışma bileşenlerle tüm platformlarda mevcut değildir.  
  
 **-Platform** kodunuzu çalışacak mimarisi hakkında varsayımlar yapmış biliyorsanız, seçeneği bazı sorunları azaltmaya. Özellikle:  
  
-   Bir 64-bit platformu hedefleyen karar ve uygulama 32-bit bir makineye çalıştırırsanız, hata iletisi çok daha önce gelen ve bu anahtar kullanmadan oluşan hatasından daha soruna daha yöneliktir.  
  
-   Ayarlarsanız `x86` bayrağı seçeneğinde ve uygulamayı daha sonra bir 64-bit makinede çalıştırın, uygulamayı yerel olarak çalıştırmak yerine WOW Subsystem çalıştıracaktır.  
  
 Bir 64-bit Windows işletim sisteminde:  
  
-   Derlenmiş derlemeler `-platform:x86` WOW64 altında çalışan 32 bit CLR üzerinde yürütülür.  
  
-   Derlenmiş olan yürütülebilir dosyalar `-platform:anycpu` 64-bit CLR üzerinde yürütülür.  
  
-   DLL ile derlenmiş `-platform:anycpu` içine yüklenen bir işlem olarak aynı CLR üzerinde yürütülür.  
  
-   İle derlenmiş yürütülebilir dosyalar `-platform:anycpu32bitpreferred` 32-bit CLR üzerinde yürütülür.  
  
 Bir Windows 64-bit sürümü çalıştırmak için uygulama geliştirme hakkında daha fazla bilgi için bkz: [64-bit uygulamalar](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Ayarlanacak - Visual Studio IDE içinde platformu  
  
1.  İçinde **Çözüm Gezgini**, proje seçme açmak **proje** menüsüne ve ardından **özellikleri**.  
  
2.  Üzerinde **derleme** sekmesini seçin veya temizleyin **tercih 32-bit** onay kutusunu veya **hedef CPU** listesinde, bir değer seçin.  
  
     Daha fazla bilgi için bkz: [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını anlatan `-platform` derleyici seçeneği.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ target (Visual Basic)](target.md)  
 [Visual Basic komut satırı derleyicisi](index.md)  
 [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
