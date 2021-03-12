---
title: Komut satırı bağımsız değişkenlerini görüntüleme-C# Programlama Kılavuzu
description: Komut satırı bağımsız değişkenlerini görüntülemeyi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 03/08/2021
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 38122f55e9886c677f6f7189ea6fe45c13c8c13b
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190261"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Komut satırı bağımsız değişkenlerini görüntüleme (C# Programlama Kılavuzu)

Komut satırındaki bir yürütülebilir dosyaya belirtilen bağımsız değişkenler, [en üst düzey deyimlerde](top-level-statements.md) veya için isteğe bağlı bir parametre aracılığıyla erişilebilir `Main` . Bağımsız değişkenler, dizeler dizisi biçiminde sağlanır. Dizinin her öğesi bir bağımsız değişken içerir. Bağımsız değişkenler arasındaki beyaz boşluk kaldırılır. Örneğin, kurgusal bir yürütülebilirin şu komut satırı çağırmaları göz önünde bulundurun:  
  
|Komut satırında giriş|Main 'e geçirilen dizelerin dizisi|  
|----------------------------|-------------------------------------|  
|**B cexecutable.exe**|a<br /><br /> kenarı<br /><br /> ,|  
|**executable.exe 1 2**|biriyle<br /><br /> ikiye|  
|**executable.exe "1 2" üç**|"one two"<br /><br /> ünden|  
  
> [!NOTE]
> Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  

 Bu örnek, komut satırı uygulamasına geçirilen komut satırı bağımsız değişkenlerini görüntüler. Gösterilen çıktı, yukarıdaki tablodaki ilk giriş içindir.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [csc.exe Kullanarak Komut Satırı Derleme](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main () ve Command-Line bağımsız değişkenleri](./index.md)
- [Ana() Dönüş Değerleri](./main-return-values.md)
