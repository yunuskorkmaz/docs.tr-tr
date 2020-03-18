---
title: Komut satırı bağımsız değişkenleri nasıl görüntülenir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712032"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Komut satırı bağımsız değişkenleri nasıl görüntülenir (C# Programlama Kılavuzu)
Komut satırında yürütülebilir bir bağımsız değişkene `Main`isteğe bağlı bir parametre ile erişilebilir. Bağımsız değişkenler bir dizi dize biçiminde sağlanır. Dizinin her öğesi bir bağımsız değişken içerir. Bağımsız değişkenler arasındaki beyaz boşluk kaldırılır. Örneğin, hayali bir yürütülebilir bu komut satırı çağrıları düşünün:  
  
|Komut satırına Giriş|Main'e geçirilen dizeleri dizisi|  
|----------------------------|-------------------------------------|  
|**icra edilebilir.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe bir iki**|"bir"<br /><br /> "iki"|  
|**executable.exe "bir iki" üç**|"one two"<br /><br /> "üç"|  
  
> [!NOTE]
> Visual Studio'da bir uygulama çalıştırırken Hata [Ayıklama Sayfasında, Proje Tasarımcısı'nda](/visualstudio/ide/reference/debug-page-project-designer)komut satırı bağımsız değişkenlerini belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, komut satırı uygulamasına geçirilen komut satırı bağımsız değişkenlerini görüntüler. Gösterilen çıktı yukarıdaki tablodaki ilk giriş içindir.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [csc.exe Kullanarak Komut Satırı Derleme](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](./index.md)
- [Ana() Dönüş Değerleri](./main-return-values.md)
