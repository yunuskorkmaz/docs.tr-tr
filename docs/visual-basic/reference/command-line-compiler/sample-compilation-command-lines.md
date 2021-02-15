---
description: 'Daha fazla bilgi edinin: örnek derleme komut satırları (Visual Basic)'
title: Örnek Derleme Komut Satırları
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: fbd35b7f12b3bee9690698a24dcb70d850081f95
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474011"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Örnek derleme komut satırları (Visual Basic)

Visual Studio içinden Visual Basic programları derlemeye alternatif olarak, çalıştırılabilir (. exe) dosyalar veya dinamik bağlantı kitaplığı (. dll) dosyaları oluşturmak için komut satırından derleme yapabilirsiniz.

Visual Basic komut satırı derleyicisi, giriş ve çıkış dosyalarını, derlemeleri ve hata ayıklama ve Önişlemci seçeneklerini denetleyen tam bir seçenek kümesini destekler. Her seçenek, iki değiştirilebilir formda mevcuttur: `-option` ve `/option` . Bu belgede yalnızca form gösterilmektedir `-option` .

Aşağıdaki tabloda, kendi kullanımı için değiştirebileceğiniz bazı örnek komut satırları listelenmektedir.

|Amaç|Kullanın|
|--------|---------|
|Dosya. vb dosyasını derleyin ve File.exe oluşturun|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|Dosya. vb dosyasını derleyin ve File.dll oluşturun|`vbc -target:library File.vb`|
|Dosya. vb dosyasını derleyin ve My.exe oluşturun|`vbc -out:My.exe File.vb`|
|File. vb derleyin ve hem bir kitaplık hem de File.dll adlı bir başvuru bütünleştirilmiş kodu oluşturun|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|Geçerli dizindeki tüm Visual Basic dosyalarını, iyileştirmelere ve `DEBUG` tanımlanan simgeye göre derleyin, File2.exe üretme|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|Logo veya uyarıları görüntülemeden bir File2.dll hata ayıklama sürümü üreten geçerli dizindeki tüm Visual Basic dosyalarını derleyin|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|Geçerli dizindeki tüm Visual Basic dosyalarını Something.dll olarak derle|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> Visual Studio IDE kullanarak bir proje oluşturduğunuzda, ilişkili **vbc** komutuyla ilgili bilgileri çıkış penceresinde derleyici seçenekleriyle birlikte görüntüleyebilirsiniz. Bu bilgileri göstermek için, [Seçenekler Iletişim kutusu, projeler ve çözümler ' i açın ve çalıştırın](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), sonra **MSBuild proje yapı çıkış ayrıntı** düzeyini **normal** veya daha yüksek ayrıntı düzeyi olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [Koşullu Derleme](../../programming-guide/program-structure/conditional-compilation.md)
