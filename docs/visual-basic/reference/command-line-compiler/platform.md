---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: db9b3d31ba9657d26c1fb76ce4002afad949a881
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301171"
---
# <a name="-platform-visual-basic"></a>-platform (Visual Basic)
Çıkış dosyası hangi ortak dil çalışma zamanı (CLR) platform sürümünü çalıştırabilirsiniz belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`x86`|Derlemenizi 32-bit, x86 ile uyumlu bir CLR tarafından çalıştırılacak derler.|  
|`x64`|Derlemenizi 64 bit CLR tarafından AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda çalıştırılması için derler.|  
|`Itanium`|Derlemenizi 64 bit CLR tarafından bir Itanium işlemci bir bilgisayarda çalıştırılması için derler.|  
|`arm`|ARM (Gelişmiş RISC makinesi) işlemciye sahip bir bilgisayarda çalıştırmak için derlemenizi derler.|  
|`anycpu`|Herhangi bir platform üzerinde çalıştırmasını derlemenizin derler. Uygulamayı Windows 32-bit sürümlerinde 32 bit uygulama olarak ve Windows 64 bit sürümlerinde 64 bit uygulama olarak çalışır. Bu bayrak varsayılan değerdir.|  
|`anycpu32bitpreferred`|Herhangi bir platform üzerinde çalıştırmasını derlemenizin derler. Uygulama bir 32 bit uygulama olarak, hem 32-bit hem de 64 bit Windows sürümlerinde çalışır. Bu bayrak, yalnızca yürütülebilir dosyalar için geçerlidir (. EXE) ve gerektiren [!INCLUDE[net_v45](~/includes/net-v45-md.md)].|  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `-platform` çıktı dosyası tarafından hedeflenen işlemci türünü belirtmek için seçeneği.  
  
 Genel olarak, .NET Framework derlemeleri Visual Basic'te yazılmış aynı platformdan bağımsız olarak çalışır. Ancak, farklı platformlarda farklı şekilde davranan bazı durumlar vardır. Bu yaygın durumlar şunlardır:  
  
-   Herhangi bir işaretçi türü gibi platforma göre boyutunu değiştiren üyeler içeren yapılar.  
  
-   Sabit boyutlar içeren işaretçi aritmetiği.  
  
-   Tanıtıcılar için `Integer` yerine <xref:System.IntPtr> kullanan yanlış platform çağrıları veya COM bildirimleri.  
  
-   Atama <xref:System.IntPtr> için `Integer`.  
  
-   Platform kullanarak çağırma veya COM birlikte çalışma bileşenlerle tüm platformlarda mevcut değildir.  
  
 **-Platform** seçeneği kodunuzun çalışacak mimarisi hakkında varsayımlar yapmış biliyorsanız, bazı sorunları azaltmak. Özellikle:  
  
-   Bir 64 bit platformları hedefleyen karar ve uygulamanın bir 32-bit makinede çalıştırılması, hata iletisi çok daha önce gelir ve bu anahtarı kullanmadan oluşan bir hata daha sorunu daha yöneliktir.  
  
-   Ayarlarsanız `x86` seçeneğinde bayrağı ve uygulamayı daha sonra bir 64-bit makinede çalıştırmak, uygulamayı yerel olarak çalıştırmak yerine WOW alt sistemi çalıştırır.  
  
 Bir 64 bit Windows işletim sisteminde:  
  
-   Derlenmiş derlemelerde `-platform:x86` WOW64 altında çalışan 32 bitlik CLR üzerinde yürütülür.  
  
-   Yürütülebilir dosyalar ile derlenmiş olan `-platform:anycpu` 64 bitlik CLR yürütülür.  
  
-   Bir DLL ile derlenmiş `-platform:anycpu` aynı CLR'yi işlem içine yüklenmiş olarak yürütülür.  
  
-   İle derlenen yürütülebilir dosyaları `-platform:anycpu32bitpreferred` 32 bitlik CLR yürütülür.  
  
 Bir Windows 64-bit sürümünü çalıştırmak için uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Ayarlanacak - Visual Studio IDE'de platformu  
  
1. İçinde **Çözüm Gezgini**, projeyi seçin açın **proje** menüsüne ve ardından **özellikleri**.  
  
2. Üzerinde **derleme** sekmesinde seçin veya temizleyin **32 bit tercih et** onay kutusunu veya **hedef CPU** listesinde, bir değer seçin.  
  
     Daha fazla bilgi için [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağı gösterilmektedir `-platform` derleyici seçeneği.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/target (Visual Basic)](target.md)
- [Visual Basic Komut Satırı Derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
