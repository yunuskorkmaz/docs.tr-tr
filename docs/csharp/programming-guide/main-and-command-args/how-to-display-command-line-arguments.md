---
title: 'Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7b9e488e84c78c8fdbf64431f42ea5797fdca916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)
Komut satırında bir yürütülebilir dosya için sağlanan bağımsız değişkenler isteğe bağlı bir parametre üzerinden erişilebilir `Main`. Bağımsız değişken bir dize dizisi biçiminde sağlanır. Dizideki her öğe bir bağımsız değişken içeriyor. Boşluk bağımsız değişkenler arasındaki kaldırılır. Örneğin, bu komut satırı çağrılarını kurgusal bir yürütülebilir dosyanın göz önünde bulundurun:  
  
|Komut satırında giriş|Ana geçirilen bir dize dizisi|  
|----------------------------|-------------------------------------|  
|**executable.exe b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe bir iki**|"tek"<br /><br /> "iki"|  
|**executable.exe "bir iki" üç**|"one two"<br /><br /> "üç"|  
  
> [!NOTE]
>  Visual Studio'da Uygulama çalışırken, komut satırı bağımsız değişkenleri belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir komut satırı uygulamaya geçirilen komut satırı bağımsız değişkenleri görüntüler. İlk giriş yukarıdaki tabloda gösterilen çıkış içindir.  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Ana() Dönüş Değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
