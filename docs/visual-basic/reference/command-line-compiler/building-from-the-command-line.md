---
title: Komut Satırından Derleme
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
ms.openlocfilehash: ec6ae3328c2042af950d1ee78a33d3de97219f10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414304"
---
# <a name="building-from-the-command-line-visual-basic"></a>Komut Satırından Derleme (Visual Basic)

Bir Visual Basic projesi bir veya daha fazla ayrı kaynak dosyadan oluşur. Derleme olarak bilinen işlem sırasında, bu dosyalar tek bir pakette birlikte getirilir; bir uygulama olarak çalıştırılabilen tek bir yürütülebilir dosyadır.

Visual Basic, Visual Studio tümleşik geliştirme ortamı (IDE) içinden program derlemeye alternatif olarak bir komut satırı derleyicisi sağlar. Komut satırı derleyicisi, IDE 'de tam özellik kümesine gerek olmayan (örneğin, sınırlı sistem belleği veya depolama alanı olan bilgisayarlar için kullanırken veya yazarken) gerekli durumlar için tasarlanmıştır.

Visual Studio IDE içinden kaynak dosyalarını derlemek için, **Derle** menüsünde **Build** komutunu seçin.

> [!TIP]
> Visual Studio IDE 'yi kullanarak proje dosyaları oluşturduğunuzda, ilişkili **vbc** komutu ve bu dosyanın anahtarları hakkında bilgileri çıkış penceresinde görüntüleyebilirsiniz. Bu bilgileri göstermek için, [Seçenekler Iletişim kutusu, projeler ve çözümler ' i açın ve çalıştırın](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), sonra **MSBuild proje yapı çıkış ayrıntı** düzeyini **normal** veya daha yüksek ayrıntı düzeyi olarak ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).

MSBuild kullanarak, bir komut isteminde proje (. vbproj) dosyalarını derleyebilirsiniz. Daha fazla bilgi için bkz. [komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference) ve [Izlenecek yol: MSBuild kullanma](/visualstudio/msbuild/walkthrough-using-msbuild).

## <a name="in-this-section"></a>Bu Bölümde

[Nasıl yapılır: komut satırı derleyicisini çağırma](how-to-invoke-the-command-line-compiler.md) \
Komut satırı derleyicisinin MS-DOS isteminde veya belirli bir alt dizinden nasıl çağırılacağını açıklar.

[Örnek derleme komut satırları](sample-compilation-command-lines.md) \
Kendi kullanımı için değiştirebileceğiniz örnek komut satırlarının bir listesini sağlar.

## <a name="related-sections"></a>İlgili Bölümler

[Visual Basic komut satırı derleyicisi](index.md) \
Alfabetik olarak veya amacına göre düzenlenmiş derleyici seçeneklerinin listesini sağlar.

[Koşullu derleme](../../programming-guide/program-structure/conditional-compilation.md) \
Kodun belirli bölümlerinin nasıl derlenebileceğinizi açıklar.

[Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
Farklı yapılarda nelerin ekleneceğini nasıl düzenleyebileceğinizi, proje özellikleri ' ni seçmenizi ve projelerin doğru sırada oluşturulmasını sağlar.
