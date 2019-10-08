---
title: -Platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 21526484b8423f9b366da64307bc44f8fb061fe9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005299"
---
# <a name="-platform-visual-basic"></a>-Platform (Visual Basic)
Ortak dil çalışma zamanının (CLR) hangi platform sürümünün çıkış dosyasını çalıştırabileceği belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`x86`|Derlemenizi 32 bit, x86 uyumlu CLR tarafından çalıştırılacak şekilde derler.|  
|`x64`|, Derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.|  
|`Itanium`|Derlemenizi, Itanium işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.|  
|`arm`|Derlemenizi ARM (Gelişmiş RıSC makinesi) işlemcisi olan bir bilgisayarda çalıştırılacak şekilde derler.|  
|`anycpu`|Derlemenizi herhangi bir platformda çalışacak şekilde derler. Uygulama Windows 'un 32 bit sürümlerinde 32 bitlik bir uygulama olarak ve Windows 'un 64 bit sürümlerinde bir 64 bit uygulama olarak çalışacaktır. Bu bayrak varsayılan değerdir.|  
|`anycpu32bitpreferred`|Derlemenizi herhangi bir platformda çalışacak şekilde derler. Uygulama, Windows 'un hem 32 bit hem de 64-bit sürümlerinde 32 bitlik bir uygulama olarak çalışacaktır. Bu bayrak yalnızca yürütülebilir dosyalar için geçerlidir (. EXE) ve .NET Framework 4,5 gerektirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çıkış dosyasının hedeflediği işlemcinin türünü belirtmek için `-platform` seçeneğini kullanın.  
  
 Genel olarak, Visual Basic yazılan .NET Framework derlemeleri platformdan bağımsız olarak aynı çalışacaktır. Ancak, farklı platformlarda farklı şekilde davranan bazı durumlar vardır. Bu ortak durumlar şunlardır:  
  
- Herhangi bir işaretçi türü gibi, platforma bağlı olarak boyutu değiştiren Üyeler içeren yapılar.  
  
- Sabit boyutlar içeren işaretçi aritmetiği.  
  
- Tanıtıcılar için `Integer` yerine <xref:System.IntPtr> kullanan yanlış platform çağrıları veya COM bildirimleri.  
  
- @No__t-0 `Integer` ' e atama.  
  
- Tüm platformlarda mevcut olmayan bileşenlerle platform Invoke veya COM birlikte çalışma kullanma.  
  
 Kodunuzun çalışacağı mimariyle ilgili varsayımlar yaptığını biliyorsanız, **-Platform** seçeneği bazı sorunları azaltır. Engelle  
  
- 64 bitlik bir platformu hedefistemediğinize karar verirseniz ve uygulama 32 bit makinede çalışıyorsa, hata iletisi daha önce gelir ve sorunu bu anahtarı kullanmadan oluşan hatadan daha da hedeflenmiştir.  
  
- Seçeneğinde `x86` bayrağını ayarlarsanız ve uygulama daha sonra bir 64 bit makinede çalışıyorsa, uygulama yerel olarak çalıştırmak yerine WOW alt sisteminde çalışır.  
  
 64 bitlik bir Windows işletim sisteminde:  
  
- @No__t-0 ile derlenen derlemeler, WOW64 altında çalışan 32 bitlik CLR üzerinde yürütülür.  
  
- @No__t-0 ile derlenen çalıştırılabilir dosyalar 64 bitlik CLR üzerinde yürütülür.  
  
- @No__t-0 ile derlenen bir DLL, yüklendiği işlemle aynı CLR üzerinde yürütülür.  
  
- @No__t-0 ile derlenen çalıştırılabilir dosyalar 32 bitlik CLR üzerinde yürütülür.  
  
 Windows 'un 64 bitlik bir sürümünde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Visual Studio IDE 'de set-platform  
  
1. **Çözüm Gezgini**, projeyi seçin, **Proje** menüsünü açın ve ardından **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesinde, **32 bit tercih** et onay kutusunu seçin veya temizleyin veya **hedef CPU** listesinden bir değer seçin.  
  
     Daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `-platform` derleyici seçeneğinin nasıl kullanılacağını göstermektedir.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/target (Visual Basic)](target.md)
- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
