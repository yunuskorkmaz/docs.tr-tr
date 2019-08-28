---
title: Komut Satırından Derleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 719ca45403ea56a655f06dbfea7c0fb7e32b34f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046435"
---
# <a name="building-from-the-command-line-visual-basic"></a>Komut Satırından Derleme (Visual Basic)

Bir Visual Basic projesi bir veya daha fazla ayrı kaynak dosyadan oluşur. Derleme olarak bilinen işlem sırasında, bu dosyalar tek bir pakette birlikte getirilir; bir uygulama olarak çalıştırılabilen tek bir yürütülebilir dosyadır.

Visual Basic, Visual Studio tümleşik geliştirme ortamı (IDE) içinden program derlemeye alternatif olarak bir komut satırı derleyicisi sağlar. Komut satırı derleyicisi, IDE 'de tam özellik kümesine gerek olmayan (örneğin, sınırlı sistem belleği veya depolama alanı olan bilgisayarlar için kullanırken veya yazarken) gerekli durumlar için tasarlanmıştır.

Visual Studio IDE içinden kaynak dosyalarını derlemek için, **Derle** menüsünde **Build** komutunu seçin.

> [!TIP]
> Visual Studio IDE 'yi kullanarak proje dosyaları oluşturduğunuzda, ilişkili **vbc** komutu ve bu dosyanın anahtarları hakkında bilgileri çıkış penceresinde görüntüleyebilirsiniz. Bu bilgileri göstermek için, [Seçenekler Iletişim kutusu, projeler ve çözümler ' i açın ve çalıştırın](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), sonra **MSBuild proje yapı çıkış ayrıntı** düzeyini **normal** veya daha yüksek ayrıntı düzeyi olarak ayarlayın. Daha fazla bilgi için [nasıl yapılır: Yapı günlüğü dosyalarını](/visualstudio/ide/how-to-view-save-and-configure-build-log-files)görüntüleyin, kaydedin ve yapılandırın.

MSBuild kullanarak, bir komut isteminde proje (. vbproj) dosyalarını derleyebilirsiniz. Daha fazla bilgi için bkz. [komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference) ve [izlenecek yol: MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild)'i kullanma.

## <a name="in-this-section"></a>Bu Bölümde

[Nasıl yapılır: Komut satırı derleyicisini çağırma](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) \
Komut satırı derleyicisinin MS-DOS isteminde veya belirli bir alt dizinden nasıl çağırılacağını açıklar.

[Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) \
Kendi kullanımı için değiştirebileceğiniz örnek komut satırlarının bir listesini sağlar.

## <a name="related-sections"></a>İlgili Bölümler

[Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md) \
Alfabetik olarak veya amacına göre düzenlenmiş derleyici seçeneklerinin listesini sağlar.

[Koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) \
Kodun belirli bölümlerinin nasıl derlenebileceğinizi açıklar.

[Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
Farklı yapılarda nelerin ekleneceğini nasıl düzenleyebileceğinizi, proje özellikleri ' ni seçmenizi ve projelerin doğru sırada oluşturulmasını sağlar.
