---
title: 'Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: a6067482b4a225abc31592affb2cfab38847cd53
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502678"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)
Komut satırında yürütülebilir bir dosya için sağlanan bağımsız değişkenler için isteğe bağlı bir parametre üzerinden erişilebilir `Main`. Bağımsız değişken bir dize dizisi biçiminde sağlanır. Dizinin her öğesinin tek bağımsız değişken içeriyor. Bağımsız değişkenler arasındaki boşluk kaldırılır. Örneğin, kurgusal bir yürütülebilir komut satırı bu çağrıları göz önünde bulundurun:  
  
|Komut satırında giriş|Ana geçirilen bir dize dizisi|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c.**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**bir executable.exe iki**|"bir"<br /><br /> "iki"|  
|**executable.exe "bir iki" üç**|"one two"<br /><br /> "üç"|  
  
> [!NOTE]
>  Visual Studio'da bir uygulamayı çalıştırırken, komut satırı bağımsız değişkenlerini belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir komut satırı uygulamaya geçirilen komut satırı bağımsız değişkenlerini görüntüler. İlk giriş yukarıdaki tabloda gösterilen çıktıya içindir.  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [Ana() Dönüş Değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
