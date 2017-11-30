---
title: "Örnek Derleme Komut Satırları (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e168d40a22ca3737bee18f966df95988a2736a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Örnek Derleme Komut Satırları (Visual Basic)
Derleme alternatif olarak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programların içinden [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], yürütülebilir dosyanın (.exe) veya dinamik bağlantı kitaplığı (.dll) dosyaları üretmek için komut satırından derleyebilirsiniz.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Komut satırı derleyicisi girdi ve çıktı dosyaları, derlemeler ve hata ayıklama denetleyen ve önişlemci seçeneklerini eksiksiz bir kümesini destekler. Her seçenek birbirinin yerine iki biçimde sağlanır: `-``option` ve `/``option`. Bu belge yalnızca gösterir `/``option` formu.  
  
 Aşağıdaki tabloda bazı örnek komut satırları kendi kullanımınız için değiştirebileceğiniz listeler.  
  
|Bitiş|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|--------|---------|  
|File.vb derlemek ve File.exe oluşturma|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|File.vb derlemek ve File.dll oluşturma|`vbc /target:library File.vb`|  
|File.vb derlemek ve My.exe oluşturma|`vbc /out:My.exe File.vb`|  
|Tüm derleme [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dosyaları en iyi duruma getirme ile geçerli dizinin üzerindeki ve `DEBUG` tanımlanmış sembol File2.exe üretme|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|Tüm derleme [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] logo veya uyarıları görüntülemeden File2.dll hata sürümü oluşturan geçerli dizindeki dosyaları|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|Tüm derleme [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Something.dll için geçerli dizindeki dosyaları|`vbc /target:library /out:Something.dll *.vb`|  
  
 Komut satırından derlerken Microsoft açıkça başvurmalıdır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] çalışma zamanı kitaplığı aracılığıyla `/reference` derleyici seçeneği.  
  
> [!TIP]
>  Visual Studio IDE kullanarak bir proje oluşturduğunuzda ilişkili ilgili bilgileri görüntüleyebilirsiniz **vbc** kendi derleyici seçenekleri çıktı penceresinde ile komutu. Bu bilgileri görüntülemek için açık [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)ve ardından **MSBuild Proje yapı çıktı ayrıntı** için **Normal** veya daha yüksek bir ayrıntı düzeyi. Daha fazla bilgi için bkz: [nasıl yapılır: görünümü, kaydetme ve yapı günlük dosyalarını Yapılandır](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
