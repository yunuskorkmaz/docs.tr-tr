---
title: Örnek Derleme Komut Satırları (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 0771ed41d6c58ce7cc98435b405f5819e45393db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916766"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Örnek derleme komut satırları (Visual Basic)
Visual Studio içinde Visual Basic programlarından derleme alternatif olarak, yürütülebilir (.exe) veya dinamik bağlantı kitaplığı (.dll) dosyaları üretmek için komut satırından derleyebilirsiniz.  
  
 Visual Basic komut satırı derleyicisi giriş denetleyen ve dosyaları, derlemeleri ve hata ayıklama ve önişlemci seçenekleri çıkış seçenekleri eksiksiz bir kümesini destekler. Her seçenek birbirinin yerine iki biçimde kullanılabilir: `-option` ve `/option`. Bu belgelerde yalnızca `-option` formu.  
  
 Aşağıdaki tabloda bazı örnek komut satırları, kendi kullanımınız için değiştirebileceğiniz listeler.  
  
|Bitiş|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|--------|---------|  
|File.vb derleyin ve File.exe oluşturma|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|File.vb derleyin ve File.dll oluşturma|`vbc -target:library File.vb`|  
|File.vb derleyin ve My.exe oluşturma|`vbc -out:My.exe File.vb`|  
|File.vb derlemek ve bir kitaplık hem File.dll adlı bir başvuru bütünleştirilmiş kodu oluşturma|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Geçerli dizindeki iyileştirmeler tüm Visual Basic dosyaları üzerinde derleyin ve `DEBUG` tanımlanmış sembol File2.exe üretme|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Geçerli dizindeki logosu veya uyarıları görüntülemeden File2.dll hata ayıklama sürümü oluşturan tüm Visual Basic dosyaları derleme|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Something.dll geçerli dizindeki tüm Visual Basic dosyaları derleme|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  Visual Studio IDE kullanarak bir proje oluşturduğunuzda, ilişkili bilgileri görüntüleyebilir **vbc** çıktı penceresinde, derleyici seçenekleri ile komutu. Bu bilgileri görüntülemek için Aç [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)ve ardından **MSBuild proje oluşturması çıkış ayrıntısı** için **Normal** veya daha yüksek bir ayrıntı düzeyi.   
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
