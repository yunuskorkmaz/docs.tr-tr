---
title: Örnek Derleme Komut Satırları (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf20e2916efd2eb10065be22c319e34ddb2bda9a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Örnek derleme komut satırları (Visual Basic)
Visual Basic programları içinden derleme alternatif olarak [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], yürütülebilir dosyanın (.exe) veya dinamik bağlantı kitaplığı (.dll) dosyaları üretmek için komut satırından derleyebilirsiniz.  
  
 Visual Basic komut satırı derleyicisi giriş denetleyen ve dosyaları, derlemeler ve hata ayıklama ve önişlemci seçenekleri çıkış seçenekleri eksiksiz bir kümesini destekler. Her seçenek birbirinin yerine iki biçimde sağlanır: `-option` ve `/option`. Bu belge yalnızca gösterir `-option` formu.  
  
 Aşağıdaki tabloda bazı örnek komut satırları kendi kullanımınız için değiştirebileceğiniz listeler.  
  
|Bitiş|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|--------|---------|  
|File.vb derlemek ve File.exe oluşturma|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|File.vb derlemek ve File.dll oluşturma|`vbc -target:library File.vb`|  
|File.vb derlemek ve My.exe oluşturma|`vbc -out:My.exe File.vb`|  
|File.vb derlemek ve kitaplığa ve File.dll adlı bir başvuru derlemesi oluşturma|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Üzerinde en iyi duruma getirme ile geçerli dizinin tüm Visual Basic dosyalarını derlemek ve `DEBUG` tanımlanmış sembol File2.exe üretme|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|Geçerli dizindeki logo veya uyarıları görüntülemeden File2.dll hata sürümü oluşturan tüm Visual Basic dosyaları derleme|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|Something.dll geçerli dizindeki tüm Visual Basic dosyaları derleme|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  Visual Studio IDE kullanarak bir proje oluşturduğunuzda ilişkili ilgili bilgileri görüntüleyebilirsiniz **vbc** kendi derleyici seçenekleri çıktı penceresinde ile komutu. Bu bilgileri görüntülemek için açık [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)ve ardından **MSBuild Proje yapı çıktı ayrıntı** için **Normal** veya daha yüksek bir ayrıntı düzeyi.   
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
