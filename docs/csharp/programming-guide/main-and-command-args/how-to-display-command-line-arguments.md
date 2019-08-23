---
title: 'Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüle C# -Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: ba732930d08c74433d6ea7b38e7dc3a9fddf594c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923858"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleC# (Programlama Kılavuzu)
Komut satırındaki bir çalıştırılabilir dosyaya girilen bağımsız değişkenlere, için `Main`isteğe bağlı bir parametre üzerinden erişilebilir. Bağımsız değişkenler, dizeler dizisi biçiminde sağlanır. Dizinin her öğesi bir bağımsız değişken içerir. Bağımsız değişkenler arasındaki beyaz boşluk kaldırılır. Örneğin, kurgusal bir yürütülebilirin şu komut satırı çağırmaları göz önünde bulundurun:  
  
|Komut satırında giriş|Main 'e geçirilen dizelerin dizisi|  
|----------------------------|-------------------------------------|  
|**çalıştırılabilir. exe a b c**|a<br /><br /> kenarı<br /><br /> ,|  
|**yürütülebilir. exe 1 2**|biriyle<br /><br /> ikiye|  
|**yürütülebilir. exe "1 2" üç**|"one two"<br /><br /> ünden|  
  
> [!NOTE]
> Visual Studio 'da bir uygulama çalıştırırken, [hata ayıklama sayfasında, proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer)' nda komut satırı bağımsız değişkenlerini belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, komut satırı uygulamasına geçirilen komut satırı bağımsız değişkenlerini görüntüler. Gösterilen çıktı, yukarıdaki tablodaki ilk giriş içindir.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [csc.exe Kullanarak Komut Satırı Derleme](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](./index.md)
- [Ana() Dönüş Değerleri](./main-return-values.md)
