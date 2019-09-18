---
title: 'Nasıl yapılır: Komut satırı derleyicisini çağır (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: a81d5b4f4eae76b0306e2d27475cb8527bda0ff2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054226"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Nasıl yapılır: Komut satırı derleyicisini çağır (Visual Basic)

Komut satırı derleyicisini, yürütülebilir dosyasının adını MS-DOS istemi olarak da bilinen komut satırına yazarak çağırabilirsiniz. Varsayılan Windows komut Isteminden derleme yaparsanız, yürütülebilir dosyanın tam yolunu yazmanız gerekir. Bu varsayılan davranışı geçersiz kılmak için, Visual Studio Geliştirici Komut İstemi kullanabilir ya da PATH ortam değişkenini değiştirebilirsiniz. Her ikisi de yalnızca derleyici adını yazarak herhangi bir dizinden derlemenize izin verir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Visual Studio için Geliştirici Komut İstemi kullanarak derleyiciyi çağırmak için

1. Microsoft Visual Studio program grubu içinde Visual Studio Araçları program klasörünü açın.

2. Visual Studio 'nun yüklüyse, makinenizde herhangi bir dizinden derleyiciye erişmek için Visual Studio Geliştirici Komut İstemi kullanabilirsiniz.

3. Visual Studio için Geliştirici Komut İstemi çağırın.

4. Komut satırında `vbc.exe` *sourceFileName* yazın ve ENTER tuşuna basın.

    Örneğin, kaynak kodunuzu adlı `SourceFiles`bir dizinde depoladıysanız, komut istemi ' ni açıp bu dizine geçmek için yazın. `cd SourceFiles` Dizinde adlı `Source.vb`bir kaynak dosyası varsa, yazarak `vbc.exe Source.vb`derleyebilirsiniz.

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Windows komut Istemi için PATH ortam değişkenini derleyiciye ayarlamak için

1. Yerel diskinizde Vbc. exe ' yi bulmak için Windows Search özelliğini kullanın.

    Derleyicinin bulunduğu dizinin tam adı Windows dizininin konumuna ve ".NET Framework" sürümünün yüklü olmasına bağlıdır. ".NET Framework" öğesinin birden fazla sürümü yüklüyse, hangi sürümün kullanılacağını (genellikle en son sürüm) belirlemelisiniz.

2. **Başlangıç** menüsünde **, Bilgisayarım ' a sağ tıklayın ve**ardından kısayol menüsünde **Özellikler** ' e tıklayın.

3. **Gelişmiş** sekmesine tıklayın ve ardından **ortam değişkenleri**' ne tıklayın.

4. **Sistem** değişkenleri bölmesinde listeden **yol** ' ı seçin ve **Düzenle**' ye tıklayın.

5. Sistem değişkenini **Düzenle** iletişim kutusunda, ekleme noktasını **değişken değer** alanındaki dizenin sonuna taşıyın ve noktalı virgül (;) yazın ardından adım 1 ' de bulunan tam dizin adı.

6. Düzenlemelerinizi onaylamak ve iletişim kutularını kapatmak için **Tamam** ' ı tıklatın.

     PATH ortam değişkenini değiştirdikten sonra, Visual Basic derleyicisini bilgisayardaki herhangi bir dizinden Windows komut Isteminde çalıştırabilirsiniz.

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Windows komut Istemi kullanarak derleyiciyi çağırmak için

1. **Başlat** menüsünde, **Donatılar** klasörüne tıklayın ve ardından **Windows komut istemi**' ni açın.

2. Komut satırında `vbc.exe` *sourceFileName* yazın ve ENTER tuşuna basın.

     Örneğin, kaynak kodunuzu adlı `SourceFiles`bir dizinde depoladıysanız, komut istemi ' ni açıp bu dizine geçmek için yazın. `cd SourceFiles` Dizinde adlı `Source.vb`bir kaynak dosyası varsa, yazarak `vbc.exe Source.vb`derleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
