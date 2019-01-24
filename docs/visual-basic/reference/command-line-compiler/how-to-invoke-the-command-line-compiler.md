---
title: 'Nasıl yapılır: (Visual Basic) komut satırı derleyicisini çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: dd5fadb9c9f248b5fb4f289bb2d24f1b085a79a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503735"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Nasıl yapılır: (Visual Basic) komut satırı derleyicisini çağırma
Komut satırına, MS-DOS İstemi olarak da bilinen yürütülebilir dosyasının adını yazarak komut satırı derleyicisini çağırabilirsiniz. Windows komut istemi varsayılan derleme yaparsanız, yürütülebilir dosyanın tam yolunu yazmanız gerekir. Bu varsayılan davranışı geçersiz kılmak için Visual Studio için geliştirici komut istemi kullanın veya yol ortam değişkenine değiştirin. Her ikisi de, derleme adını yazarak herhangi bir dizinden derleme olanak tanır.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Visual Studio için geliştirici komut istemi kullanarak derleyici çağırmak için  
  
1.  Microsoft Visual Studio program grubu içinde Visual Studio Araçları program klasörü açın.  
  
2.  Visual Studio yüklüyse derleyici makinenizde, herhangi bir dizinden erişmek için Visual Studio için geliştirici Komut İstemi'ni kullanabilirsiniz.  
  
3.  Visual Studio için geliştirici komut istemi çağırın.  
  
4.  Komut satırında `vbc.exe` *sourceFileName* yazıp ENTER tuşuna basın.  
  
     Örneğin, kaynak kodunuzu adlı dizinde depolanan `SourceFiles`, türü ve komut istemi açmak `cd SourceFiles` bu dizine gidin. Dizin adlı bir kaynak dosyası içeriyorsa `Source.vb`, yazarak derleme `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>PATH ortam değişkenine derleyicisi için Windows komut istemi ayarlamak için  
  
1.  Yerel diskinizde Vbc.exe bulmak için Windows Search özelliğini kullanın.  
  
     Derleyici bulunduğu dizinin tam adı, Windows dizin konumunu ve ".NET Framework'ün" sürüm bağlıdır. ".NET Framework'ün" birden fazla sürümü varsa, hangi sürümün (genellikle en son sürüm) kullanılacağını belirlemeniz gerekir.  
  
2.  Öğesinden, **Başlat** menüsünde sağ **Bilgisayarım**ve ardından **özellikleri** kısayol menüsünden.  
  
3.  Tıklayın **Gelişmiş** sekmesine ve ardından **ortam değişkenlerini**.  
  
4.  İçinde **sistem** değişkenleri bölmesinde **yolu** listesi ve **Düzenle**.  
  
5.  İçinde **düzenleme sistemi** değişken iletişim kutusunda, dizenin sonuna ekleme noktasını Taşı **değişken değeri** alan ve noktalı virgül (;) yazın ardından adım 1'de bulunan tam dizin adı.  
  
6.  Tıklayın **Tamam** yaptığınız düzenlemeleri onaylamak ve iletişim kutularını kapatmak için.  
  
     PATH ortam değişkenine değiştirdikten sonra Visual Basic Derleyicisi Windows komut isteminde herhangi bir dizinden bilgisayarda çalıştırabilirsiniz.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Windows komut istemi kullanarak derleyici çağırmak için  
  
1.  Gelen **Başlat** menüsünde tıklatın **Donatılar** klasörünü açın ve ardından açık **Windows Komut İstemi**.  
  
2.  Komut satırında `vbc.exe` *sourceFileName* yazıp ENTER tuşuna basın.  
  
     Örneğin, kaynak kodunuzu adlı dizinde depolanan `SourceFiles`, türü ve komut istemi açmak `cd SourceFiles` bu dizine gidin. Dizin adlı bir kaynak dosyası içeriyorsa `Source.vb`, yazarak derleme `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Koşullu Derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
